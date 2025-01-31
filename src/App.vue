<template>
  <div id="app">
    <SideBar id="side-bar" />
    <div class="main-content">
      <MobileTopNav id="mobile-top-nav" />
      <DashboardView />
    </div>
  </div>
</template>

<script>
import SideBar from "@/components/layout/SideBar.vue";
import DashboardView from "@/views/DashboardView.vue";
import MobileTopNav from "./components/layout/MobileTopNav.vue";

export default {
  name: "App",
  components: {
    SideBar,
    DashboardView,
    MobileTopNav,
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
  height: 100dvh;
  width: 100dvw;
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.main-content {
  flex-grow: 1;
  overflow-y: auto;
  width: 100%;
}

#mobile-top-nav {
  display: none;
}

@media (max-width: 550px) {
  #side-bar {
    display: none;
  }
  #mobile-top-nav {
    display: flex;
  }
}
</style>
