<template>
  <header class="mobile-top-nav">
    <!-- Logo -->
    <div class="logo">
      <span class="icon">💚</span>
      <span class="dashboard-name">Dashboard</span>
    </div>

    <!-- Hamburger Button -->
    <button class="hamburger-btn" @click="toggleMenu">
      <i class="fas fa-bars"></i>
    </button>

    <!-- Dropdown Menu -->
    <div v-if="menuVisible" class="dropdown-menu">
      <SideBarItem
        v-for="(item, index) in menuItems"
        :key="index"
        :icon="item.icon"
        :text="item.text"
        :isActive="activeTab === item.text"
        @setActive="selectItem(item.text)"
      />
    </div>
  </header>
</template>

<script>
import SideBarItem from "./SideBarItem.vue";

export default {
  components: { SideBarItem },
  data() {
    return {
      menuVisible: false,
      activeTab: "Dashboard",
      menuItems: [
        { icon: "fas fa-home", text: "Dashboard" },
        { icon: "fas fa-box", text: "Product" },
        { icon: "fas fa-warehouse", text: "Inventory" },
        { icon: "fas fa-users", text: "Customers" },
        { icon: "fas fa-star", text: "Review" },
        { icon: "fas fa-credit-card", text: "Payment" },
        { icon: "fas fa-plug", text: "Integration" },
        { icon: "fas fa-cog", text: "Settings" },
        { icon: "fas fa-question-circle", text: "Help" },
        { icon: "fas fa-user-cog", text: "Users" },
        { icon: "fas fa-sign-out-alt", text: "Logout" },
      ],
    };
  },
  methods: {
    toggleMenu() {
      this.menuVisible = !this.menuVisible;
    },
    selectItem(tab) {
      this.activeTab = tab;
      this.menuVisible = false;
    },
  },
};
</script>

<style scoped>
.mobile-top-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #15161b;
  color: white;
  padding: 10px 15px;
  font-size: 16px;
  position: relative;
  border-bottom: 1px solid #eee;
}

.logo {
  display: flex;
  align-items: center;
}

.dashboard-name {
  margin-left: 5px;
  font-weight: 100;
}

.hamburger-btn {
  background: none;
  border: none;
  cursor: pointer;
  color: white;
  font-size: 24px;
}

.dropdown-menu {
  position: absolute;
  top: 50px;
  left: 0;
  width: 100%;
  background-color: #15161b;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  padding: 10px 0;
}

.dropdown-menu .sidebar-item {
  padding: 10px 15px;
  font-size: 14px;
  color: white;
  display: flex;
  align-items: center;
  cursor: pointer;
  width: 100%;
}

.dropdown-menu .sidebar-item:hover {
  background-color: #444;
}

.dropdown-menu .sidebar-item i {
  margin-right: 10px;
}

/* Hide dropdown menu by default */
.dropdown-menu {
  display: none;
}

/* Show dropdown menu when visible */
.dropdown-menu {
  display: block;
}
</style>
