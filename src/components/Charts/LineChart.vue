<template>
  <div class="chart-container">
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script>
import { defineComponent, reactive, onMounted, ref, watch } from "vue";
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

export default defineComponent({
  setup() {
    const chartData = reactive({
      labels: [
        "Sep 07",
        "Sep 08",
        "Sep 09",
        "Sep 10",
        "Sep 11",
        "Sep 12",
        "Sep 13",
      ],
      datasets: [
        {
          label: "Orders",
          data: [2000, 4000, 3000, 6000, 5000, 8000, 7000],
          borderColor: "#2E7D32",
          backgroundColor: "#30a378",
          borderWidth: 3,
          tension: 0.4,
          pointRadius: 0,
        },
        {
          label: "Income Growth",
          data: [1000, 2000, 1500, 3500, 2500, 4500, 4000],
          borderColor: "#81C784",
          backgroundColor: "#4adf21",
          borderWidth: 3,
          tension: 0.4,
          pointRadius: 0,
        },
      ],
    });

    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false,
      scales: {
        y: {
          beginAtZero: true,
          min: 0,
          max: 10000,
          ticks: {
            stepSize: 2000,
            callback: (value) => `${value / 1000}K`,
          },
          grid: {
            display: false,
            drawBorder: false,
            drawTicks: false,
          },
        },
        x: {
          grid: {
            display: true,
            drawBorder: false,
            drawTicks: false,
          },
        },
      },
      plugins: {
        legend: {
          display: true,
          position: "top",
          labels: {
            font: {
              family: "Poppins",
            },
            boxWidth: 20,
            boxHeight: 10,
            padding: 10,
            usePointStyle: true,
          },
          onClick: (e, legendItem, legend) => {
            const index = legendItem.datasetIndex;
            const chart = legend.chart;
            const dataset = chart.data.datasets[index];
            dataset.hidden = !dataset.hidden;
            chart.update();
          },
        },
      },
    };

    const chartCanvas = ref(null);
    let chartInstance = null;

    onMounted(() => {
      if (chartCanvas.value) {
        chartInstance = new Chart(chartCanvas.value, {
          type: "line",
          data: chartData,
          options: chartOptions,
        });
      }
    });

    watch(
      () => chartCanvas.value,
      (newCanvas) => {
        if (newCanvas && chartInstance) {
          chartInstance.destroy();
          chartInstance = new Chart(newCanvas, {
            type: "line",
            data: chartData,
            options: chartOptions,
          });
        }
      },
      { immediate: true }
    );

    return { chartCanvas };
  },
});
</script>

<style scoped>
.chart-container {
  width: 100%;
}

canvas {
  max-height: 250px;
  width: 100%;
}
</style>
