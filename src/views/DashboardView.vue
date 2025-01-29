<template>
  <div class="dashboard-view">
    <!-- Import NavBar Component -->
    <NavBar />
    <!-- This will display the navigation bar -->

    <!-- Main Content -->
    <div class="main-content">
      <!-- Content sections like heading, buttons, cards, etc. -->
    </div>
  </div>
</template>

<script>
// Importing the NavBar component
import NavBar from "@/components/layout/NavBar.vue"; // Adjust path as needed

export default {
  name: "DashboardView",
  components: {
    NavBar, // Register NavBar component
  },
};
</script>

<style scoped>
/* Main Dashboard View */
.dashboard-view {
  display: flex;
  flex-direction: column;
  width: 100%;
}

/* Main Content area styling */
.main-content {
  flex-grow: 1;
  padding: 20px;
}
</style>
