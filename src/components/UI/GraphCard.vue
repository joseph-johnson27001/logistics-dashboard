<template>
  <div class="graph-card">
    <div class="graph-card-header">
      <div class="top-card-container">
        <h2 class="title">{{ graphTitle }}</h2>
        <p class="total-deliveries">
          Total Number Of {{ totalType }}: {{ total }}
        </p>
      </div>
      <div class="info-container">
        <select class="dropdown">
          <option>January</option>
        </select>
      </div>
    </div>
    <slot name="graph"></slot>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "GraphCard",
  props: {
    graphTitle: {
      type: String,
      required: true,
    },
    total: {
      type: Number,
      required: true,
    },
    totalType: {
      type: String,
      required: true,
    },
  },
});
</script>

<style scoped>
.graph-card {
  background: white;
  padding: 20px;
  border-radius: 5px;
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
  font-size: 16px;
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
  margin-top: 2px;
  font-size: 13px;
  color: rgba(47, 43, 61, 0.55);
}

.dropdown {
  padding: 10px 15px;
  font-weight: 600;
  font-family: "Inter";
  background-color: #e8e6fc;
  color: #8b81f3;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  outline: none;
}

.dropdown:hover {
  background-color: #c0bbf7;
}
</style>
