<template>
  <transition name="slide-fade">
    <div v-if="isVisible" class="mobile-nav">
      <div class="close-btn" @click="closeMenu">&times;</div>
      <ul>
        <li @click="navigateTo()">Home</li>
        <li @click="navigateTo()">Dashboard</li>
        <li @click="navigateTo()">Shipments</li>
        <li @click="navigateTo()">Fleet</li>
        <li @click="navigateTo()">Inventory</li>
        <li @click="navigateTo()">Reports</li>
        <li @click="navigateTo()">Analytics</li>
        <li @click="navigateTo()">Support</li>
        <li @click="navigateTo()">Settings</li>
        <li @click="navigateTo()">Logout</li>
      </ul>
    </div>
  </transition>
</template>

<script>
export default {
  name: "MobileNav",
  data() {
    return {
      windowWidth: window.innerWidth,
      isVisible: false,
    };
  },
  mounted() {
    window.addEventListener("resize", this.handleResize);
    if (this.windowWidth < 700) {
      this.isVisible = true;
    }
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth >= 700) {
        this.isVisible = false;
      }
    },
    closeMenu() {
      this.isVisible = false;
    },
    navigateTo() {
      this.closeMenu();
    },
  },
};
</script>

<style scoped>
.mobile-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.95);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.close-btn {
  position: absolute;
  top: 15px;
  right: 20px;
  font-size: 2rem;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  padding: 15px;
  font-size: 1.2rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 10px;
  width: 100%;
  justify-content: flex-start;
}

li:hover {
  background-color: rgba(0, 0, 0, 0.05);
}

.fas {
  font-size: 1.5rem;
}

.slide-fade-enter,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
