<template>
  <div class="stat-card" :style="{ backgroundColor: backgroundColor }">
    <div class="card-header">
      <h3>{{ title }}</h3>
      <p class="card-value">{{ value }}</p>
    </div>
    <div class="card-footer">
      <!-- Bottom Left Percentage Change -->
      <div class="percentage-container">
        <div
          class="percentage-change"
          :style="{
            color: changeColorText,
          }"
        >
          <i :class="chevronIconClass" :style="{ color: changeColorText }"></i>
          {{ percentage }}
        </div>
      </div>

      <!-- Bottom Right Additional Value -->
      <div class="additional-value-container" v-if="additionalValue">
        <p class="additional-value">{{ additionalValue }}</p>
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
    additionalValue: String,
  },
  computed: {
    changeColorText() {
      return this.percentage.startsWith("-") ? "#f3635d" : "#5cc49f";
    },
    chevronIconClass() {
      return this.percentage.startsWith("-")
        ? "fas fa-chevron-down"
        : "fas fa-chevron-up";
    },
  },
};
</script>

<style scoped>
.stat-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 15px 20px;
  border-radius: 12px;
  border: 1px solid #ddd;
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
  font-size: 22px;
  font-weight: 600;
  margin: 5px 0px 10px 0px;
}

.card-footer {
  display: flex;
  justify-content: space-between;
}

.percentage-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.percentage-change {
  display: flex;
  align-items: center;
  padding: 5px 10px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 600;
  background-color: white;
}

.percentage-change i {
  margin-right: 8px;
  font-size: 10px;
}

.additional-value-container {
  padding: 5px 10px;
}

.additional-value {
  font-size: 12px;
  font-weight: 600;
  color: #333;
  margin: 0;
}
</style>
