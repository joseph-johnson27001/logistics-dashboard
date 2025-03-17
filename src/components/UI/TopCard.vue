<template>
  <div class="top-card">
    <!-- Left Section (Search) -->
    <div class="search-area">
      <i class="fas fa-search"></i>
      <input type="text" placeholder="Search..." />
    </div>

    <!-- Right Section (Icons & Profile) -->
    <div class="icon-area">
      <i class="far fa-bell notification-icon">
        <span class="notification-dot"></span>
      </i>
      <i class="far fa-comment-alt"></i>
      <i class="far fa-calendar-check"></i>

      <!-- Profile Image with Online Indicator -->
      <div class="profile">
        <img src="https://randomuser.me/api/portraits/men/4.jpg" alt="User" />
        <span class="online-indicator"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopCard",
};
</script>

<style scoped>
.top-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  padding: 10px 20px;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}

.search-area {
  display: flex;
  align-items: center;
  flex-grow: 1;
}

.search-area i {
  margin-right: 10px;
  color: #555;
}

.search-area input {
  flex-grow: 1;
  border: none;
  outline: none;
  font-size: 16px;
  background: none;
  font-family: "Inter", sans-serif;
}

.icon-area {
  display: flex;
  align-items: center;
  gap: 20px;
}

.icon-area i {
  font-size: 20px;
  cursor: pointer;
  color: #555;
  position: relative;
}

.notification-icon {
  position: relative;
}

.notification-dot {
  width: 8px;
  height: 8px;
  background: red;
  border-radius: 50%;
  position: absolute;
  top: 0px;
  right: 0px;
}

.profile {
  position: relative;
  width: 40px;
  height: 40px;
}

.profile img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
}

.online-indicator {
  width: 8px;
  height: 8px;
  background: #28c76f;
  border-radius: 50%;
  position: absolute;
  bottom: 0px;
  right: 0px;
  border: 2px solid white;
}
</style>
