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
      </button>
    </div>

    <!-- Navigation Menu -->
    <nav class="menu">
      <p class="menu-heading" v-if="!isCollapsed">GENERAL</p>
      <SideBarItem
        icon="fas fa-home"
        text="Dashboard"
        :isActive="activeTab === 'Dashboard'"
        @setActive="setActiveTab('Dashboard')"
      />
      <SideBarItem
        icon="fas fa-box"
        text="Product"
        :isActive="activeTab === 'Product'"
        @setActive="setActiveTab('Product')"
      />
      <SideBarItem
        icon="fas fa-warehouse"
        text="Inventory"
        :isActive="activeTab === 'Inventory'"
        @setActive="setActiveTab('Inventory')"
      />
      <SideBarItem
        icon="fas fa-users"
        text="Customers"
        :isActive="activeTab === 'Customers'"
        @setActive="setActiveTab('Customers')"
      />
      <SideBarItem
        icon="fas fa-star"
        text="Review"
        :isActive="activeTab === 'Review'"
        @setActive="setActiveTab('Review')"
      />
      <SideBarItem
        icon="fas fa-credit-card"
        text="Payment"
        :isActive="activeTab === 'Payment'"
        @setActive="setActiveTab('Payment')"
      />
      <SideBarItem
        icon="fas fa-plug"
        text="Integration"
        :isActive="activeTab === 'Integration'"
        @setActive="setActiveTab('Integration')"
      />

      <p class="menu-heading" v-if="!isCollapsed">ACCOUNT</p>
      <SideBarItem
        icon="fas fa-cog"
        text="Settings"
        :isActive="activeTab === 'Settings'"
        @setActive="setActiveTab('Settings')"
      />
      <SideBarItem
        icon="fas fa-question-circle"
        text="Help"
        :isActive="activeTab === 'Help'"
        @setActive="setActiveTab('Help')"
      />
      <SideBarItem
        icon="fas fa-user-cog"
        text="Manage Users"
        :isActive="activeTab === 'Manage Users'"
        @setActive="setActiveTab('Manage Users')"
      />
    </nav>

    <!-- Logout Button -->
    <div class="logout">
      <SideBarItem
        icon="fas fa-sign-out-alt"
        text="Logout"
        :isActive="activeTab === 'Logout'"
        @setActive="setActiveTab('Logout')"
      />
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
      activeTab: "Dashboard",
    };
  },
  methods: {
    toggleSidebar() {
      this.isCollapsed = !this.isCollapsed;
    },
    setActiveTab(tab) {
      this.activeTab = tab;
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
  width: 60px;
}

/* Header Section */
.sidebar-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 10px 30px 10px;
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
  cursor: pointer;
  color: #8a8c8b;
  font-size: 16px;
}

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
  margin-bottom: 10px;
}

.sidebar.collapsed .menu i {
  font-size: 24px;
  display: block;
  text-align: center;
  width: 100%;
  margin: auto;
}

.sidebar.collapsed .menu-heading {
  display: none;
}

.sidebar.collapsed .sidebar-header .logo {
  justify-content: center;
  width: 100%;
}

.sidebar.collapsed .menu i {
  font-size: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 25px;
  height: 25px;
  margin: auto;
  box-sizing: border-box;
}

.sidebar.collapsed .sidebar-header .dashboard-name {
  display: none;
}

.sidebar.collapsed .menu {
  padding: 0;
}

.sidebar.collapsed .sidebar-item {
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 10px 10px;
  height: 35px;
  width: 50px;
  margin: 0px;
}

.sidebar.collapsed .logo {
  display: none;
}

.sidebar.collapsed .toggle-btn {
  display: flex;
  justify-self: center;
  margin: auto;
  width: 25px;
  height: 25px;
}
</style>
