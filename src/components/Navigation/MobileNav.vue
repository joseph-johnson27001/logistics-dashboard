<template>
  <transition name="slide-fade">
    <div v-if="isVisible" class="mobile-nav">
      <div class="close-btn" @click="closeMenu">&times;</div>
      <ul>
        <li v-for="(item, index) in navItems" :key="index" @click="closeMenu">
          <div class="icon-container">
            <i :class="item.icon"></i>
          </div>
          {{ item.name }}
        </li>
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
      navItems: [
        { name: "Home", icon: "fas fa-home" },
        { name: "Dashboard", icon: "fas fa-tachometer-alt" },
        { name: "Shipments", icon: "fas fa-shipping-fast" },
        { name: "Fleet", icon: "fas fa-truck" },
        { name: "Inventory", icon: "fas fa-cogs" },
        { name: "Reports", icon: "fas fa-chart-line" },
        { name: "Analytics", icon: "fas fa-chart-pie" },
        { name: "Support", icon: "fas fa-life-ring" },
        { name: "Settings", icon: "fas fa-cogs" },
        { name: "Logout", icon: "fas fa-sign-out-alt" },
      ],
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
  background-color: rgba(0, 0, 0, 0.7);
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  z-index: 1000;
  padding-top: 50px;
  transition: opacity 0.1s ease;
  text-align: center;
}

.close-btn {
  position: absolute;
  top: 15px;
  right: 20px;
  font-size: 2rem;
  color: #fff;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
  width: 100%;
}

li {
  padding: 15px 20px;
  font-size: 1.1rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 15px;
  width: 100%;
  justify-content: flex-start;
  color: #fff;
  transition: background-color 0.3s ease;
}

li:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.fas {
  font-size: 1.5rem;
}

.icon-container {
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.slide-fade-enter,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
