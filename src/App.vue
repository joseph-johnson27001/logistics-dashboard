<template>
  <div id="app">
    <SideBar />
    <div class="main-content">
      <TopCard />
      <div class="content"></div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import TopCard from "./components/UI/TopCard.vue";

export default {
  name: "App",
  components: {
    SideBar,
    TopCard,
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
</style>
