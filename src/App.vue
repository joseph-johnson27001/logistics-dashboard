<template>
  <div id="app">
    <SideBar />
    <div class="main-content">
      <TopCard />
      <div class="content">
        <div class="kpi-container">
          <KpiCard
            v-for="(kpi, index) in kpis"
            :key="index"
            :icon="kpi.icon"
            :value="kpi.value"
            :title="kpi.title"
            :change="kpi.change"
            :backgroundColorLight="kpi.backgroundColorLight"
            :backgroundColorDark="kpi.backgroundColorDark"
            :style="{ borderBottomColor: kpi.backgroundColorDark }"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import TopCard from "./components/UI/TopCard.vue";
import KpiCard from "./components/UI/KpiCard.vue";

export default {
  name: "App",
  components: {
    SideBar,
    TopCard,
    KpiCard,
  },
  data() {
    return {
      kpis: [
        {
          title: "On Route Vehicles",
          value: 234,
          change: 18.2,
          icon: "fas fa-truck-moving",
          backgroundColorLight: "#e0e7ff",
          backgroundColorDark: "#5a67d8",
        },
        {
          title: "Vehicles with Issues",
          value: 12,
          change: -8.5,
          icon: "fas fa-exclamation-circle",
          backgroundColorLight: "#ffe6e6",
          backgroundColorDark: "#d9534f",
        },
        {
          title: "Deviated from Route",
          value: 7,
          change: -5.3,
          icon: "fas fa-route",
          backgroundColorLight: "#fef3c7",
          backgroundColorDark: "#f59e0b",
        },
        {
          title: "Late Vehicles",
          value: 29,
          change: 6.7,
          icon: "fas fa-clock",
          backgroundColorLight: "#d1fae5",
          backgroundColorDark: "#10b981",
        },
      ],
    };
  },
};
</script>

<style>
body {
  margin: 0px !important;
  scrollbar-width: none;
  font-family: "Inter", sans-serif;
}

::-webkit-scrollbar {
  display: none;
}
</style>

<style scoped>
#app {
  display: flex;
  min-height: 100vh;
}

.main-content {
  flex-grow: 1;
  padding: 20px;
  background-color: #f6f5f8;
}

.content {
  margin-top: 20px;
}

.kpi-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}
</style>
