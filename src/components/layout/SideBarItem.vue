<template>
  <div class="sidebar-item" :class="{ active: isActive }" @click="setActive">
    <i :class="[icon]"></i>
    <span v-if="!$parent.isCollapsed">{{ text }}</span>
  </div>
</template>

<script>
export default {
  props: {
    icon: String,
    text: String,
    isActive: Boolean,
  },
  methods: {
    setActive() {
      this.$emit("setActive");
    },
  },
};
</script>

<style scoped>
.sidebar-item {
  display: flex;
  align-items: center;
  padding: 10px 10px;
  color: #ececec;
  cursor: pointer;
  transition: background 0.2s;
  margin: 5px 10px 5px 5px;
  border-radius: 4px;
}
.sidebar-item:hover,
.sidebar-item.active {
  background: rgba(255, 255, 255, 0.1);
}
.sidebar-item i {
  height: 17px;
  width: 15px;
  text-align: center;
  margin-right: 15px;
  color: #8a8c8b;
}

.sidebar-item span {
  font-weight: 100;
  font-size: 13px;
}
</style>
