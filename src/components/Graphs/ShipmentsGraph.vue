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
  name: "ShipmentsGraph",
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
            label: "Deliveries",
            data: [28, 48, 40, 19, 86, 27, 90, 69, 68, 45, 50, 65],
            borderColor: "#9e6cfd",
            backgroundColor: "rgba(0, 0, 0, 0)",
            pointBackgroundColor: "white",
            fill: false,
            tension: 0.2,
            type: "line",
            borderWidth: 3,
            pointRadius: 5,
            z: 10,
          },
          {
            label: "Shipments",
            data: [65, 59, 80, 81, 56, 55, 40, 65, 78, 65, 50, 55],
            backgroundColor: "#ffb400",
            borderColor: "#ffb400",
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
