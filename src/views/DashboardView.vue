<template>
  <div class="dashboard-view">
    <NavBar />

    <!-- Main Content -->
    <div class="main-content"></div>
  </div>
</template>

<script>
import NavBar from "@/components/layout/NavBar.vue";

export default {
  name: "DashboardView",
  components: {
    NavBar,
  },
};
</script>

<style scoped>
.dashboard-view {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.main-content {
  flex-grow: 1;
  padding: 20px;
}
</style>
