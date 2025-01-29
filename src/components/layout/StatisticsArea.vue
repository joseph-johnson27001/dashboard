<template>
  <div class="statistics-area">
    <div class="stat-cards">
      <StatCard
        title="Revenue"
        value="$245,450"
        percentage="14.9%"
        backgroundColor="#fcf0e4"
        additionalValue="(+43.21%)"
      />
      <StatCard
        title="New Customers"
        value="684"
        percentage="- 8.6%"
        backgroundColor="#edf5e8"
      />
      <StatCard
        title="Purchase Rate"
        value="75.12%"
        percentage="25.4%"
        backgroundColor="#eaf0fe"
        additionalValue="(+20.11%)"
      />
      <StatCard
        title="Average Value"
        value="$2,412.23"
        percentage="35.2%"
        backgroundColor="#ecf5f4"
        additionalValue="(+$754)"
      />
      <StatCard
        title="Conversion Rate"
        value="32.65%"
        percentage="- 12.42%"
        backgroundColor="#f6eced"
      />
    </div>
  </div>
</template>

<script>
import StatCard from "@/components/ui/StatCard.vue";

export default {
  name: "StatisticsArea",
  components: {
    StatCard,
  },
};
</script>

<style scoped>
.statistics-area {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.stat-cards {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
  width: 100%;
}
</style>
