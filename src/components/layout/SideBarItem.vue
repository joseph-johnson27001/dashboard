<template>
  <div class="sidebar-item">
    <i :class="[icon]"></i>
    <span v-if="!$parent.isCollapsed">{{ text }}</span>
  </div>
</template>

<script>
export default {
  props: {
    icon: String,
    text: String,
  },
};
</script>

<style scoped>
.sidebar-item {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  color: white;
  cursor: pointer;
  transition: background 0.2s;
}
.sidebar-item:hover {
  background: rgba(255, 255, 255, 0.1);
}
.sidebar-item i {
  width: 25px;
  text-align: center;
}
</style>
