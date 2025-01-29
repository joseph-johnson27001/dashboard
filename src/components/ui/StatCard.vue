<template>
  <div class="stat-card" :style="{ backgroundColor: backgroundColor }">
    <div class="card-header">
      <h3>{{ title }}</h3>
      <p class="card-value">{{ value }}</p>
    </div>
    <div class="card-footer">
      <div class="percentage-change" :style="{ color: changeColor }">
        {{ percentage }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StatCard",
  props: {
    title: String,
    value: String,
    percentage: String,
    backgroundColor: String,
  },
  computed: {
    changeColor() {
      return this.percentage.startsWith("-") ? "red" : "green";
    },
  },
};
</script>

<style scoped>
.stat-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 15px;
  border-radius: 12px;
}

.card-header {
  display: flex;
  flex-direction: column;
}

.card-header h3 {
  font-size: 14px;
  font-weight: 100;
  margin: 0;
}

.card-value {
  font-size: 20px;
  font-weight: 600;
  margin-top: 5px;
}

.percentage-change {
  font-size: 12px;
  font-weight: 600;
  text-align: left;
  margin-top: 10px;
}
</style>
