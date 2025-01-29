<template>
  <aside :class="['sidebar', { collapsed: isCollapsed }]">
    <!-- Top Section with Logo and Toggle Button -->
    <div class="sidebar-header">
      <div class="logo">
        <span class="icon" v-if="!isCollapsed">💚</span>
        <span v-if="!isCollapsed" class="dashboard-name">Dashboard</span>
      </div>
      <button class="toggle-btn" @click="toggleSidebar">
        <i class="fas fa-bars"></i>
        <!-- Always show the hamburger icon -->
      </button>
    </div>

    <!-- Navigation Menu -->
    <nav class="menu">
      <p class="menu-heading" v-if="!isCollapsed">GENERAL</p>
      <SideBarItem icon="fas fa-home" text="Dashboard" />
      <SideBarItem icon="fas fa-box" text="Product" />
      <SideBarItem icon="fas fa-warehouse" text="Inventory" />
      <SideBarItem icon="fas fa-users" text="Customers" />
      <SideBarItem icon="fas fa-star" text="Review" />
      <SideBarItem icon="fas fa-credit-card" text="Payment" />
      <SideBarItem icon="fas fa-plug" text="Integration" />

      <p class="menu-heading" v-if="!isCollapsed">ACCOUNT</p>
      <SideBarItem icon="fas fa-cog" text="Settings" />
      <SideBarItem icon="fas fa-question-circle" text="Help" />
      <SideBarItem icon="fas fa-user-cog" text="Manage Users" />
    </nav>

    <!-- Logout Button -->
    <div class="logout">
      <SideBarItem icon="fas fa-sign-out-alt" text="Logout" />
    </div>
  </aside>
</template>

<script>
import SideBarItem from "./SideBarItem.vue";

export default {
  components: { SideBarItem },
  data() {
    return {
      isCollapsed: false,
    };
  },
  methods: {
    toggleSidebar() {
      this.isCollapsed = !this.isCollapsed;
    },
  },
};
</script>

<style scoped>
/* Sidebar Container */
.sidebar {
  width: 250px;
  height: 100vh;
  background-color: #15161b;
  color: white;
  display: flex;
  flex-direction: column;
  transition: width 0.3s ease;
  overflow: hidden;
}
.sidebar.collapsed {
  width: 80px;
}

/* Header Section */
.sidebar-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 0px 30px 10px;
  font-size: 16px;
}
.logo {
  display: flex;
  align-items: center;
}

.dashboard-name {
  margin-left: 5px;
  font-weight: 100;
}
.toggle-btn {
  background: none;
  border: none;
  color: white;
  cursor: pointer;
  color: #8a8c8b;
  font-size: 16px;
  padding-right: 10px;
}

/* Menu */
.menu {
  flex-grow: 1;
  padding: 15px 0;
}
.menu-heading {
  padding: 0px 15px;
  font-size: 12px;
  text-transform: uppercase;
  opacity: 0.7;
}
.logout {
  margin-top: auto;
  padding: 10px 10px;
}
</style>
