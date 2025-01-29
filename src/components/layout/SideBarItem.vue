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
  padding: 10px 5px;
  color: #ececec;
  cursor: pointer;
  transition: background 0.2s;
  margin: 0px 10px;
  border-radius: 10px;
}
.sidebar-item:hover {
  background: rgba(255, 255, 255, 0.1);
}
.sidebar-item i {
  height: 17px;
  width: 15px;
  margin-right: auto;
  text-align: center;
  margin-right: 15px;
  color: #8a8c8b;
}

.sidebar-item span {
  font-weight: 100;
  font-size: 13px;
}
</style>
