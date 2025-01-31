<template>
  <div class="summary-card">
    <div class="header">
      <h3 class="title">{{ selectedRange }}</h3>
      <div class="dropdown">
        <div class="dropdown-trigger" @click="toggleDropdown">
          <span>{{ selectedRange }}</span>
          <span class="chevron">▼</span>
        </div>
        <div v-if="dropdownVisible" class="dropdown-options">
          <div
            v-for="(option, index) in options"
            :key="index"
            class="dropdown-option"
            @click="selectRange(option)"
          >
            {{ option }}
          </div>
        </div>
      </div>
    </div>

    <div class="divider"></div>

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
    const dropdownVisible = ref(false);

    const options = [
      "Last 7 Days",
      "Last 30 Days",
      "Last 6 Months",
      "Last 1 Year",
    ];

    const toggleDropdown = () => {
      dropdownVisible.value = !dropdownVisible.value;
    };

    const selectRange = (option) => {
      selectedRange.value = option;
      dropdownVisible.value = false;
    };

    return {
      selectedRange,
      dropdownVisible,
      options,
      toggleDropdown,
      selectRange,
    };
  },
};
</script>

<style scoped>
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

.dropdown {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  position: relative;
  width: 150px;
}

.dropdown-trigger {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fefefe;
  border: 1px solid #eee;
  border-radius: 8px;
  padding: 5px 0px;
  width: 100%;
  cursor: pointer;
  padding-left: 10px;
}

.chevron {
  font-size: 12px;
  margin-right: 10px;
  color: #555;
}

.dropdown-options {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: white;
  border: 1px solid #eee;
  border-radius: 8px;
  width: 160px;
  max-height: 200px;
  overflow-y: auto;
  z-index: 1;
}

.dropdown-option {
  padding: 10px 15px;
  background-color: white;
  color: #15161b;
  font-size: 14px;
  cursor: pointer;
}

.dropdown-option:hover {
  background-color: #f1f1f1;
}

.divider {
  height: 1px;
  background-color: #eee;
  margin: 10px 0;
}

@media (max-width: 600px) {
  .dropdown {
    margin-left: auto;
    width: 80px;
  }

  .dropdown-trigger {
    padding: 4px 6px;
    font-size: 12px;
    width: 70px;
  }

  .dropdown-options {
    width: 100%;
  }

  .dropdown-option {
    padding: 6px 10px;
    font-size: 11px;
  }

  .chevron {
    font-size: 9px;
  }
}
</style>
