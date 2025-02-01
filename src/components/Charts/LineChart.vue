<template>
  <div class="chart-container">
    <canvas ref="chartCanvas"></canvas>
  </div>
</template>

<script>
import { defineComponent, onMounted, ref, reactive, watch } from "vue";
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

export default defineComponent({
  setup() {
    const chartCanvas = ref(null);
    let chartInstance = null;

    // Define chart data reactively
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
      datasets: [],
    });

    // Define chart options
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
            padding: 10,
            callback: (value) => {
              return value === 0 ? "" : `${value / 1000}K`;
            },
          },
          grid: {
            display: false,
            drawBorder: false,
            drawTicks: false,
            borderDash: [5, 5],
          },
        },
        x: {
          grid: {
            display: true,
            drawBorder: false,
            drawTicks: false,
            drawOnChartArea: true,
            borderDash: [5, 5],
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
            boxHeight: 8,
            padding: 10,
            usePointStyle: true,
          },
        },
      },
    };

    onMounted(() => {
      if (chartCanvas.value) {
        const ctx = chartCanvas.value.getContext("2d");

        const ordersGradient = ctx.createLinearGradient(0, 0, 0, 200);
        ordersGradient.addColorStop(0, "rgba(24, 144, 255, 0.3)");
        ordersGradient.addColorStop(1, "rgba(24, 144, 255, 0)");

        const incomeGradient = ctx.createLinearGradient(0, 0, 0, 240);
        incomeGradient.addColorStop(0, "rgba(48, 163, 120, 0.3)");
        incomeGradient.addColorStop(1, "rgba(48, 163, 120, 0)");

        chartData.datasets = [
          {
            label: "Orders",
            data: [7000, 6000, 6500, 6000, 5000, 8000, 7000],
            borderColor: "#1890ff",
            backgroundColor: ordersGradient,
            borderWidth: 3,
            tension: 0.2,
            pointRadius: 0,
            fill: true,
          },
          {
            label: "Income Growth",
            data: [4000, 4000, 1500, 3500, 2500, 4500, 4000],
            borderColor: "#30a378",
            backgroundColor: incomeGradient,
            borderWidth: 3,
            tension: 0.2,
            pointRadius: 0,
            fill: true,
          },
        ];

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
  padding: 10px 0px;
  height: 280px;
}

canvas {
  width: 100% !important;
  height: 100% !important;
}
</style>
