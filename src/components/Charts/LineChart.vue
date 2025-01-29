<template>
  <div class="chart-container">
    <LineChart
      ref="lineChart"
      :chart-data="chartData"
      :chart-options="chartOptions"
    />
  </div>
</template>

<script>
import { defineComponent, reactive, onMounted } from "vue";
import { Chart, registerables } from "chart.js";
import { LineChart } from "vue-chart-3";

Chart.register(...registerables);

export default defineComponent({
  components: { LineChart },
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
          borderColor: "#2E7D32", // Dark Green
          backgroundColor: "rgba(46, 125, 50, 0.2)",
          borderWidth: 2,
          tension: 0.4, // Smooth curves
        },
        {
          label: "Income Growth",
          data: [1000, 2000, 1500, 3500, 2500, 4500, 4000],
          borderColor: "#81C784", // Light Green
          backgroundColor: "rgba(129, 199, 132, 0.2)",
          borderWidth: 2,
          tension: 0.4,
        },
      ],
    });

    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false, // Allow manual height control
      scales: {
        y: {
          beginAtZero: true,
          min: 0,
          max: 10000,
          ticks: {
            callback: (value) => `${value / 1000}K`, // Format as 0K, 10K
          },
          grid: {
            display: false, // No horizontal grid lines
          },
        },
        x: {
          grid: {
            display: false,
          },
        },
      },
      plugins: {
        legend: {
          display: true,
          position: "top",
        },
      },
    };

    // On mounted, target the canvas to apply custom styles
    onMounted(() => {
      const canvas = document.querySelector("canvas");
      if (canvas) {
        canvas.style.maxHeight = "250px";
        canvas.style.width = "100%"; // Optionally set width as well if you need
        canvas.style.objectFit = "cover"; // Ensures proper scaling within the max-height
      }
    });

    return { chartData, chartOptions };
  },
});
</script>

<style scoped>
.chart-container {
  width: 100%;
}
</style>
