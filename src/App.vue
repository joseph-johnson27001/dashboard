<template>
  <div id="app">
    <SideBar />
    <div class="main-content">
      <router-view />
    </div>
  </div>
</template>

<script>
import SideBar from "@/components/layout/SideBar.vue";

export default {
  name: "App",
  components: {
    SideBar,
  },
};
</script>

<style>
body {
  padding: 0px;
  margin: 0px;
}

#app {
  display: flex;
  height: 100vh;
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.main-content {
  flex-grow: 1;
  background: #f4f4f4;
  overflow-y: auto;
}
</style>
