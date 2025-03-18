<template>
  <div class="delivery-performance-card">
    <div class="delivery-stat" v-for="(stat, index) in stats" :key="index">
      <div
        class="stat-icon-container"
        :style="{ backgroundColor: stat.backgroundColorLight }"
      >
        <i :class="stat.icon" :style="{ color: stat.iconColor }"></i>
      </div>
      <div class="stat-content">
        <div class="stat-title">{{ stat.title }}</div>
        <div class="stat-change">
          <span :class="stat.changeClass">
            <i :class="stat.changeIcon"></i> {{ stat.change }}%
          </span>
        </div>
      </div>
      <div class="stat-value">{{ stat.value }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DeliveryPerformance",
  data() {
    return {
      stats: [
        {
          title: "Delivery Success Rate",
          change: 35.6,
          value: "95%",
          icon: "fas fa-check-circle",
          iconColor: "#887ef2",
          backgroundColorLight: "#e8e6fc",
          changeClass: "positive",
          changeIcon: "fas fa-chevron-up", // Chevron for positive change
        },
        {
          title: "Average Delivery Time",
          change: -2.15,
          value: "3 days",
          icon: "fas fa-clock",
          iconColor: "#f59e0b",
          backgroundColorLight: "#fef3c7",
          changeClass: "negative",
          changeIcon: "fas fa-chevron-down", // Chevron for negative change
        },
        {
          title: "Customer Satisfaction",
          change: 5.7,
          value: "4.5/5",
          icon: "fas fa-smile",
          iconColor: "#10b981",
          backgroundColorLight: "#d1fae5",
          changeClass: "positive",
          changeIcon: "fas fa-chevron-up", // Chevron for positive change
        },
      ],
    };
  },
};
</script>

<style scoped>
.delivery-performance-card {
  display: flex;
  flex-direction: column;
  background-color: white;
  border-radius: 5px;
}

.delivery-stat {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 0;
}

.stat-icon-container {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  background-color: #f0f0f0;
}

.stat-icon-container i {
  font-size: 24px;
}

.stat-content {
  flex-grow: 1;
  margin-left: 15px;
}

.stat-title {
  font-weight: bold;
  font-size: 16px;
  color: #333;
}

.stat-change {
  margin-top: 5px;
  font-size: 14px;
}

.stat-change .positive {
  color: #28c76f;
}

.stat-change .negative {
  color: #ea5455;
}

.stat-value {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}
</style>
