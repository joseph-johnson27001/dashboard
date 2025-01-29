<template>
  <div class="dashboard-view">
    <NavBar />

    <!-- Main Content -->
    <div class="content-area">
      <HeadingArea />
    </div>
  </div>
</template>

<script>
import NavBar from "@/components/layout/NavBar.vue";
import HeadingArea from "@/components/layout/HeadingArea.vue";

export default {
  name: "DashboardView",
  components: {
    NavBar,
    HeadingArea,
  },
};
</script>

<style scoped>
.dashboard-view {
  display: flex;
  flex-direction: column;
}

.content-area {
  padding: 20px;
}
</style>
