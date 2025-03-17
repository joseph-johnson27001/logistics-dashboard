<template>
  <div class="graph-container">
    <canvas ref="chart"></canvas>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { Chart } from "chart.js";
import {
  CategoryScale,
  LinearScale,
  BarElement,
  LineElement,
  BarController,
  LineController,
  Title,
  Tooltip,
  Legend,
  PointElement,
} from "chart.js";

Chart.register(
  CategoryScale,
  LinearScale,
  BarElement,
  LineElement,
  BarController,
  LineController,
  Title,
  Tooltip,
  Legend,
  PointElement
);

Chart.defaults.font.family = '"Inter", sans-serif';

export default defineComponent({
  name: "OrdersGraph",
  data() {
    return {
      chartData: {
        labels: [
          "Jan 1",
          "Jan 2",
          "Jan 3",
          "Jan 4",
          "Jan 5",
          "Jan 6",
          "Jan 7",
          "Jan 8",
          "Jan 9",
          "Jan 10",
          "Jan 11",
          "Jan 12",
        ],
        datasets: [
          {
            label: "Orders",
            data: [30, 45, 38, 50, 80, 55, 70, 60, 75, 85, 90, 100],
            borderColor: "#FF8C00", // Dark orange border color
            backgroundColor: "rgba(255, 140, 0, 0.2)", // Light orange background fill
            pointBackgroundColor: "white",
            fill: true,
            tension: 0.4,
            type: "line",
            borderWidth: 3,
            pointRadius: 5,
            z: 10,
          },
          {
            label: "New Orders",
            data: [50, 40, 60, 90, 70, 65, 80, 95, 75, 85, 90, 110],
            backgroundColor: "#42A5F5", // Light blue for bars
            borderColor: "#1E88E5", // Darker blue border color
            borderWidth: 1,
            type: "bar",
            borderRadius: 4,
            maxBarThickness: 25,
          },
        ],
      },
    };
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const ctx = this.$refs.chart.getContext("2d");
      new Chart(ctx, {
        type: "bar",
        data: this.chartData,
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            x: {
              grid: {
                display: false,
              },
            },
            y: {
              grid: {
                display: true,
                borderColor: "rgba(169, 169, 169, 0.5)",
                borderWidth: 0.5,
                lineWidth: 0.5,
                borderDash: [5, 5],
              },
              ticks: {
                beginAtZero: true,
                stepSize: 20,
              },
            },
          },
          plugins: {
            legend: {
              labels: {
                usePointStyle: true,
                pointStyle: "circle",
              },
            },
          },
        },
      });
    },
  },
});
</script>

<style scoped>
.graph-container {
  width: 100%;
  height: 300px;
  position: relative;
}

canvas {
  width: 100% !important;
  height: 100% !important;
}
</style>
