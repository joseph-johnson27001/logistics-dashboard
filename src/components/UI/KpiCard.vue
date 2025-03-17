<template>
  <div class="kpi-card">
    <div
      class="icon-container"
      :style="{ backgroundColor: backgroundColorLight }"
    >
      <i :class="icon" :style="{ color: backgroundColorDark }"></i>
    </div>
    <div class="kpi-content">
      <div class="kpi-value">{{ value }}</div>
      <div class="kpi-title">{{ title }}</div>
      <div class="kpi-change">
        <span :class="changeClass">{{ change }}%</span>
        <span class="kpi-subtext"> than last week</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "KpiCard",
  props: {
    icon: String,
    value: Number,
    title: String,
    change: Number,
    backgroundColorLight: String,
    backgroundColorDark: String,
  },
  computed: {
    changeClass() {
      return this.change >= 0 ? "positive" : "negative";
    },
  },
};
</script>

<style scoped>
.kpi-card {
  display: flex;
  align-items: center;
  background: white;
  padding: 15px;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  border-bottom: 2px solid;
  transition: transform 0.2s ease-in-out;
  flex: 1;
}

.icon-container {
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
}

.icon-container i {
  font-size: 24px;
}

.kpi-content {
  margin-left: 15px;
  display: flex;
  flex-direction: column;
}

.kpi-value {
  font-size: 22px;
  font-weight: bold;
  color: #333;
}

.kpi-title {
  color: grey;
  font-size: 14px;
}

.kpi-change {
  margin-top: 5px;
  font-size: 14px;
}

.kpi-change .positive {
  color: #28c76f;
}

.kpi-change .negative {
  color: #ea5455;
}

.kpi-subtext {
  color: lightgrey;
  font-size: 12px;
  margin-left: 5px;
}
</style>
