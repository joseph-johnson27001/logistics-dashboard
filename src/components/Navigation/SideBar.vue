<template>
  <div class="sidebar">
    <div class="sidebar-title">
      <h1>Logistics</h1>
    </div>
    <ul>
      <li
        v-for="(item, index) in menuItems"
        :key="index"
        :class="{
          active: activeItem === item.name,
          'logout-item': item.name === 'logout',
        }"
        @click="setActive(item.name)"
      >
        <i :class="item.icon"></i> {{ item.label }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  data() {
    return {
      activeItem: "dashboard",
      menuItems: [
        {
          name: "dashboard",
          label: "Dashboard",
          icon: "far fa-envelope-open",
        },
        {
          name: "shipments",
          label: "Shipments",
          icon: "far fa-calendar",
        },
        {
          name: "fleet",
          label: "Fleet Management",
          icon: "far fa-lightbulb",
        },

        {
          name: "inventory",
          label: "Inventory",
          icon: "far fa-file",
        },
        {
          name: "reports",
          label: "Reports",
          icon: "far fa-chart-bar",
        },
        {
          name: "analytics",
          label: "Analytics",
          icon: "fas fa-chart-line",
        },
        {
          name: "support",
          label: "Support",
          icon: "far fa-user-circle",
        },
        {
          name: "settings",
          label: "Settings",
          icon: "far fa-save",
        },
        {
          name: "logout",
          label: "Logout",
          icon: "fas fa-sign-out-alt",
        },
      ],
    };
  },
  methods: {
    setActive(item) {
      this.activeItem = item;
    },
    logout() {
      console.log("Logging out...");
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 260px;
  background-color: rgb(255, 255, 255);
  color: rgba(47, 43, 61, 0.9);
  height: 100%;
  padding-top: 20px;
  position: fixed;
  font-size: 15px;
  box-shadow: 0 2px 8px rgba(47, 43, 61, 0.12);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.sidebar-title {
  padding: 0px 20px;
  color: rgba(47, 43, 61, 0.9);
}

.sidebar-title h1 {
  font-family: "Unica One", sans-serif;
  font-weight: 400;
  margin: 0;
  color: #0b508b;
}

.sidebar ul {
  list-style: none;
  padding: 0px 5px;
  flex-grow: 1;
}

.sidebar ul li {
  padding: 8px;
  line-height: 23px;
  cursor: pointer;
  border-radius: 5px;
  margin: 7px;
  display: flex;
  align-items: center;
}

.sidebar ul {
  list-style: none;
  padding: 0px 5px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.sidebar ul li.logout-item {
  margin-top: auto;
  margin-bottom: 20px;
}

.sidebar ul li:hover {
  background-color: #f0f0f1;
}

.sidebar ul li.logout-item:hover i {
  color: #ff4d4f;
}

.sidebar ul li.active {
  background: linear-gradient(
    270deg,
    rgba(115, 103, 240, 0.7),
    rgb(115, 103, 240)
  );
  box-shadow: 0 2px 6px rgba(115, 103, 240, 0.3);
  color: white;
}

.sidebar ul li i {
  margin-right: 10px;
  margin-left: 5px;
  color: rgba(47, 43, 61, 0.9);
  font-size: 16px;
}

.sidebar ul li.active i {
  color: white;
}
</style>
