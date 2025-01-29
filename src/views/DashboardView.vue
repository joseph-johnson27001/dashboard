<template>
  <div class="dashboard-view">
    <NavBar />

    <!-- Main Content -->
    <div class="content-area">
      <HeadingArea />
      <StatisticsArea />
    </div>
  </div>
</template>

<script>
import NavBar from "@/components/layout/NavBar.vue";
import HeadingArea from "@/components/layout/HeadingArea.vue";
import StatisticsArea from "@/components/layout/StatisticsArea.vue";

export default {
  name: "DashboardView",
  components: {
    NavBar,
    HeadingArea,
    StatisticsArea,
  },
};
</script>

<style scoped>
.dashboard-view {
  display: flex;
  flex-direction: column;
}

.content-area {
  padding: 20px 30px;
}
</style>
