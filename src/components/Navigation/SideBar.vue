<template>
  <div class="sidebar">
    <ul>
      <li
        v-for="(item, index) in menuItems"
        :key="index"
        :class="{ active: activeItem === item.name }"
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
          icon: "far fa-envelope-open",
        },
        {
          name: "fleet",
          label: "Fleet Management",
          icon: "far fa-arrow-alt-circle-right",
        },
        {
          name: "settings",
          label: "Settings",
          icon: "far fa-arrow-alt-circle-right",
        },
      ],
    };
  },
  methods: {
    setActive(item) {
      this.activeItem = item;
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 260px;
  background-color: #fff;
  color: rgba(47, 43, 61, 0.9);
  height: 100vh;
  padding-top: 20px;
  position: fixed;
  font-size: 15px;
  box-shadow: 0 2px 8px rgba(47, 43, 61, 0.12);
}

.sidebar ul {
  list-style: none;
  padding: 5px;
  margin-top: 20px;
}

.sidebar ul li {
  padding: 8px;
  line-height: 23px;
  cursor: pointer;
  border-radius: 5px;
  margin: 8px;
  display: flex;
  align-items: center;
}

.sidebar ul li:hover {
  background-color: #f0f0f1;
}

.sidebar ul li.active {
  background: linear-gradient(
    270deg,
    rgba(115, 103, 240, 0.7),
    rgb(115, 103, 240) 100%
  );
  box-shadow: 0 2px 6px rgba(115, 103, 240, 0.3);
  color: white;
}

.sidebar ul li i {
  margin-right: 10px;
  margin-left: 10px;
  color: rgba(47, 43, 61, 0.9);
}

.sidebar ul li.active i {
  color: white;
}
</style>
