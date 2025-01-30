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
          data: [7000, 6000, 6500, 6000, 5000, 8000, 7000],
          borderColor: "#30a378",
          backgroundColor: "#30a378",
          borderWidth: 3,
          tension: 0.4,
          pointRadius: 0,
        },
        {
          label: "Income Growth",
          data: [4000, 4000, 1500, 3500, 2500, 4500, 4000],
          borderColor: "#4adf21",
          backgroundColor: "#4adf21",
          borderWidth: 3,
          tension: 0.4,
          pointRadius: 0,
        },
      ],
    });

    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false, // Allows the chart to fill its container
      scales: {
        y: {
          beginAtZero: true,
          min: 0,
          max: 10000,
          ticks: {
            stepSize: 2000,
            callback: (value) => {
              if (value === 0) {
                return "";
              }
              return `${value / 1000}K`;
            },
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
  position: relative;
  height: 250px; /* Ensure chart takes available height within the parent */
}

canvas {
  width: 100% !important;
  height: 100% !important; /* Allow canvas to fill its container */
}
</style>
