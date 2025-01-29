<template>
  <div class="card">
    <!-- Header Section (Moved from LineChart.vue) -->
    <div class="header">
      <h3 class="title">Summary</h3>
      <div class="dropdown">
        <select v-model="selectedRange">
          <option>Last 7 Days</option>
        </select>
        <span class="chevron">▼</span>
      </div>
    </div>

    <!-- Chart Component -->
    <LineChart :selected-range="selectedRange" />
  </div>
</template>

<script>
import { ref } from "vue";
import LineChart from "@/components/Charts/LineChart.vue";

export default {
  name: "SummaryCard",
  components: { LineChart },
  setup() {
    const selectedRange = ref("Last 7 Days");
    return { selectedRange };
  },
};
</script>

<style scoped>
/* Card Styling */
.card {
  padding: 20px;
  border: 1px solid #eee;
  border-radius: 12px;
  background-color: white;
}

/* Header */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.title {
  font-size: 16px;
  font-weight: bold;
  color: black;
}

/* Dropdown */
.dropdown {
  display: flex;
  align-items: center;
  background-color: #f7f7f7;
  border: 1px solid #eee;
  border-radius: 8px;
  padding: 5px 10px;
  position: relative;
}

select {
  background: transparent;
  border: none;
  font-size: 14px;
  cursor: pointer;
  appearance: none;
  padding-right: 20px;
}

select:focus {
  outline: none;
}

.chevron {
  font-size: 12px;
  margin-left: -20px;
  pointer-events: none;
  color: #555;
}
</style>
