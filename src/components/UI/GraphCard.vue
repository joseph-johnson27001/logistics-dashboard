<template>
  <div class="graph-card">
    <div class="graph-card-header">
      <div class="top-card-container">
        <h2 class="title">Shipment Statistics</h2>
        <p class="total-deliveries">
          Total number of deliveries: {{ totalDeliveries }}
        </p>
      </div>
      <div class="info-container">
        <select class="dropdown">
          <option>Option 1</option>
          <option>Option 2</option>
        </select>
      </div>
    </div>
    <!-- Importing the ShipmentsGraph component here -->
    <ShipmentsGraph />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import ShipmentsGraph from "../Graphs/ShipmentsGraph.vue"; // Corrected import

export default defineComponent({
  name: "GraphCard",
  components: {
    ShipmentsGraph,
  },
  data() {
    return {
      totalDeliveries: 153,
    };
  },
});
</script>

<style scoped>
.graph-card {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}

.graph-card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.title {
  color: rgba(47, 43, 61, 0.9);
  font-weight: 400;
  font-size: 18px;
  margin-bottom: 2px;
  margin-top: 0px;
}

.top-card-container {
  display: block;
}

.info-container {
  display: flex;
  align-items: center;
}

.total-deliveries {
  font-size: 15px;
  margin-top: 2px;
  color: rgba(47, 43, 61, 0.55);
}

.dropdown {
  padding: 5px 10px;
  background-color: #9e6cfd;
  color: #fff;
  border: 1px solid #fff;
  border-radius: 5px;
  cursor: pointer;
}
</style>
