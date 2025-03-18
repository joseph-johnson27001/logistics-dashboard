<template>
  <div class="vehichle-overview-table">
    <table>
      <tr
        v-for="(row, index) in rows"
        :key="index"
        :class="{ 'no-border-bottom': index === rows.length - 1 }"
      >
        <td class="icon-text">
          <div class="icon-container">
            <i :class="row.icon" :style="{ color: row.color }"></i>
          </div>
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
          color: "#4CAF50",
          time: "2hr 10min",
          percentage: "39.7%",
        },
        {
          label: "Unloading",
          icon: "far fa-arrow-alt-circle-down",
          color: "#FF9800",
          time: "3hr 15min",
          percentage: "28.3%",
        },
        {
          label: "Loading",
          icon: "far fa-arrow-alt-circle-up",
          color: "#2196F3",
          time: "1hr 24min",
          percentage: "17.4%",
        },
        {
          label: "Waiting",
          icon: "fa-regular fa-clock",
          color: "#F44336",
          time: "5hr 19min",
          percentage: "14.6%",
        },
      ],
    };
  },
};
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
}

td {
  padding: 10px;
}

td.icon-text {
  display: flex;
  color: rgba(47, 43, 61, 0.9);
  align-items: center;
  gap: 10px;
  font-size: 14px;
}

.icon-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 24px;
}

td.time {
  font-weight: 400;
}

td.time,
td.percentage {
  text-align: right;
  font-size: 14px;
}

tr {
  font-size: 15px;
  line-height: 1.5;
  cursor: pointer;
}

tr:hover {
  background-color: #f5f5f5;
}

tr .percentage {
  font-weight: 600;
  color: rgba(47, 43, 61, 0.7);
  color: #0b508b;
}

table tr:not(.no-border-bottom) {
  border-bottom: 1px solid #ddd;
}

i {
  font-size: 18px;
}

@media (max-width: 768px) {
  td.icon-text {
    font-size: 14px;
  }
  td.time,
  td.percentage {
    font-size: 14px;
  }
  i {
    font-size: 16px;
  }
}

@media (max-width: 480px) {
  td.icon-text {
    font-size: 12px;
    gap: 5px;
  }
  td.time,
  td.percentage {
    font-size: 12px;
  }
  i {
    font-size: 14px;
  }
  td {
    padding: 6px;
  }
}
</style>
