<template>
  <div class="vehichle-overview-table">
    <table>
      <tr
        v-for="(row, index) in rows"
        :key="index"
        :class="{ 'no-border-bottom': index === rows.length - 1 }"
      >
        <td class="icon-text"><i :class="row.icon"></i> {{ row.label }}</td>
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
          icon: "fa-regular fa-car",
          time: "2hr 10min",
          percentage: "39.7%",
        },
        {
          label: "Unloading",
          icon: "fa-regular fa-circle-down",
          time: "3hr 15min",
          percentage: "28.3%",
        },
        {
          label: "Loading",
          icon: "fa-regular fa-circle-up",
          time: "1hr 24min",
          percentage: "17.4%",
        },
        {
          label: "Waiting",
          icon: "fa-regular fa-clock",
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

table tr:not(.no-border-bottom) {
  border-bottom: 1px solid #ddd;
}
</style>
