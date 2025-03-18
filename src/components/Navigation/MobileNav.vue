<template>
  <transition name="slide-fade">
    <div v-if="isVisible" class="mobile-nav">
      <div class="close-btn" @click="closeMenu">&times;</div>
      <ul>
        <li><i class="fas fa-home"></i> Home</li>
        <li><i class="fas fa-tachometer-alt"></i> Dashboard</li>
        <li><i class="fas fa-shipping-fast"></i> Shipments</li>
        <li><i class="fas fa-truck"></i> Fleet</li>
        <li><i class="fas fa-cogs"></i> Inventory</li>
        <li><i class="fas fa-chart-line"></i> Reports</li>
        <li><i class="fas fa-chart-pie"></i> Analytics</li>
        <li><i class="fas fa-life-ring"></i> Support</li>
        <li><i class="fas fa-cogs"></i> Settings</li>
        <li><i class="fas fa-sign-out-alt"></i> Logout</li>
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
  transition: opacity 0.3s ease, transform 0.3s ease-in-out;
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

li i {
  font-size: 1.3rem;
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
