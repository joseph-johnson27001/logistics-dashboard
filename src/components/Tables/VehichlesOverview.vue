<template>
  <div class="vehichle-overview-table">
    <table>
      <tr
        v-for="(row, index) in rows"
        :key="index"
        :class="{ 'no-border-bottom': index === rows.length - 1 }"
      >
        <td class="icon-text">
          <i :class="row.icon" :style="{ color: row.color }"></i>
          {{ row.label }}
        </td>
        <td class="time">{{ row.time }}</td>
        <td class="percentage">{{ row.percentage }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "VehichleOverviewTable",
  data() {
    return {
      rows: [
        {
          label: "On the way",
          icon: "fas fa-car-side",
          color: "#4CAF50", // Green
          time: "2hr 10min",
          percentage: "39.7%",
        },
        {
          label: "Unloading",
          icon: "far fa-arrow-alt-circle-down",
          color: "#FF9800", // Orange
          time: "3hr 15min",
          percentage: "28.3%",
        },
        {
          label: "Loading",
          icon: "far fa-arrow-alt-circle-up",
          color: "#2196F3", // Blue
          time: "1hr 24min",
          percentage: "17.4%",
        },
        {
          label: "Waiting",
          icon: "fa-regular fa-clock",
          color: "#F44336", // Red
          time: "5hr 19min",
          percentage: "14.6%",
        },
      ],
    };
  },
};
</script>

<style scoped>
.vehichle-overview-table {
  width: 100%;
}

table {
  width: 100%;
  border-collapse: collapse;
}

td {
  padding: 10px;
}

td.icon-text {
  display: flex;
  align-items: center;
  gap: 10px;
}

td.time,
td.percentage {
  text-align: right;
}

tr {
  color: rgba(47, 43, 61, 0.9);
  font-size: 15px;
}

tr .time {
  font-weight: 600;
}

tr .percentage {
  color: rgba(47, 43, 61, 0.7);
}

table tr:not(.no-border-bottom) {
  border-bottom: 1px solid #ddd;
}

i {
  font-size: 18px; /* Adjust icon size */
}
</style>
