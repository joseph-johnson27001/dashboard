<template>
  <div class="card">
    <!-- Header Section -->
    <div class="header">
      <h3 class="title">Summary</h3>
      <div class="dropdown">
        <select v-model="selectedRange">
          <option>Last 7 Days</option>
          <option>Last 30 Days</option>
          <option>Last 90 Days</option>
          <option>Last 6 Months</option>
          <option>Last 1 Year</option>
        </select>
        <span class="chevron">▼</span>
      </div>
    </div>

    <!-- Divider -->
    <div class="divider"></div>

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
  padding: 20px 20px 0px 20px;
  border: 1px solid #eee;
  border-radius: 8px;
  background-color: white;
  height: 350px;
}

/* Header */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.title {
  font-size: 16px;
  font-weight: 400;
  color: #15161b;
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
  width: 150px; /* Set a fixed width for consistency */
}

select {
  background: transparent;
  border: none;
  font-size: 14px;
  cursor: pointer;
  appearance: none;
  padding: 5px 10px;
  width: 100%;
  color: #15161b;
  font-weight: 400;
}

select:focus {
  outline: none;
}

/* Custom Arrow (chevron) */
.chevron {
  font-size: 12px;
  margin-left: -20px;
  pointer-events: none;
  color: #555;
}

/* Style for select options to match the select box */
option {
  padding: 10px 15px;
  background-color: white;
  color: #15161b;
  border: 1px solid #eee;
  border-radius: 8px;
  font-size: 14px;
}

option:hover {
  background-color: #f1f1f1;
}

/* Remove default dropdown arrow */
select::-ms-expand {
  display: none;
}

/* Divider */
.divider {
  height: 1px;
  background-color: #eee;
  margin: 10px 0;
}
</style>
