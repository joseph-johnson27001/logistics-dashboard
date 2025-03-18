<template>
  <div class="statistics-card">
    <div class="statistics-card-header">
      <h2 class="title">{{ title }}</h2>
      <p class="subtitle">{{ subtitle }}</p>
    </div>
    <div class="statistics-card-body">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "StatisticsCard",
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
  },
});
</script>

<style scoped>
.statistics-card {
  background: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}

.statistics-card-header {
  margin-bottom: 15px;
}

.title {
  color: rgba(47, 43, 61, 0.9);
  font-weight: 400;
  font-size: 16px;
  margin-bottom: 2px;
  margin-top: 0px;
}

.subtitle {
  margin-top: 2px;
  margin-bottom: 5px;
  font-size: 13px;
  color: rgba(47, 43, 61, 0.55);
}

.statistics-card-body {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
}
</style>
