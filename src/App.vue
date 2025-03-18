<template>
  <div id="app">
    <SideBar />
    <div class="main-content">
      <div class="content">
        <TopCard />
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
        <div class="second-container">
          <GraphCard
            :graphTitle="'Orders'"
            :total="totalOrders"
            totalType="Orders"
          >
            <template #graph>
              <OrdersGraph />
            </template>
          </GraphCard>

          <GraphCard
            :graphTitle="'Shipments'"
            :total="totalDeliveries"
            totalType="Shipments"
          >
            <template #graph>
              <ShipmentsGraph />
            </template>
          </GraphCard>
        </div>

        <div class="bottom-container">
          <!-- Vehichle Overview Card -->
          <StatisticsCard
            title="Vehichle Overview"
            subtitle="232 Currently Active Vehichles"
          >
            <div class="vehichles-details">
              <VehichleOverviewTable />
            </div>
          </StatisticsCard>

          <StatisticsCard
            title="Delivery Performance"
            subtitle="12% Increase This month"
          >
          </StatisticsCard>

          <!-- Orders By Countries Card -->
          <StatisticsCard
            title="Orders By Countries"
            subtitle="62 Deliveries In Progress"
          >
            <div class="orders-by-countries-details">
              <OrdersByCountry />
            </div>
          </StatisticsCard>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import TopCard from "./components/UI/TopCard.vue";
import KpiCard from "./components/UI/KpiCard.vue";
import GraphCard from "./components/UI/GraphCard.vue";
import ShipmentsGraph from "./components/Graphs/ShipmentsGraph.vue";
import OrdersGraph from "./components/Graphs/OrdersGraph.vue";
import StatisticsCard from "./components/UI/StatisticsCard.vue";
import VehichleOverviewTable from "./components/Tables/VehichlesOverview.vue";
import OrdersByCountry from "./components/Tables/OrdersByCountry.vue";

export default {
  name: "App",
  components: {
    SideBar,
    TopCard,
    KpiCard,
    GraphCard,
    ShipmentsGraph,
    OrdersGraph,
    StatisticsCard,
    VehichleOverviewTable,
    OrdersByCountry,
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
      totalOrders: 230,
      totalDeliveries: 153,
    };
  },
};
</script>

<style>
body {
  margin: 0px !important;
  scrollbar-width: none;
  font-family: "Inter", sans-serif;
  overflow-y: hidden;
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
  background-color: #f6f5f8;
}

.content {
  padding: 20px;
  height: 100dvh;
  overflow-y: scroll;
  box-sizing: border-box;
}

.kpi-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-top: 20px;
}

.second-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-top: 20px;
  gap: 20px;
}

.bottom-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  margin-top: 20px;
  gap: 20px;
}

.vehichles-details {
  width: 100%;
}

.orders-by-countries-details {
  width: 100%;
}

@media (max-width: 1400px) {
  .bottom-container {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 1024px) {
  .second-container {
    grid-template-columns: 1fr;
  }
  .kpi-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .kpi-container {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
