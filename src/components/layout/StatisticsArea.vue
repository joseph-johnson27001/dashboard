<template>
  <div class="statistics-area">
    <div class="stat-cards">
      <StatCard
        v-for="(stat, index) in stats"
        :key="index"
        :title="stat.title"
        :value="stat.value"
        :percentage="stat.percentage"
        :backgroundColor="stat.backgroundColor"
        :additionalValue="stat.additionalValue"
      />
    </div>
  </div>
  <div class="cards-layout">
    <div class="card-row" v-for="(row, rowIndex) in cardRows" :key="rowIndex">
      <div v-for="(card, cardIndex) in row" :key="cardIndex" class="card">
        <component :is="card.component" />
      </div>
    </div>
  </div>
</template>

<script>
import StatCard from "@/components/ui/StatCard.vue";
import SummaryCard from "../ui/SummaryCard.vue";
import ProductCard from "../ui/ProductCard.vue";
import RecentOrderCard from "../ui/RecentOrderCard.vue";
import WeeklyCustomerCard from "../ui/WeeklyCustomerCard.vue";

export default {
  name: "StatisticsArea",
  components: {
    StatCard,
    SummaryCard,
    ProductCard,
    RecentOrderCard,
    WeeklyCustomerCard,
  },
  data() {
    return {
      stats: [
        {
          title: "Revenue",
          value: "$245,450",
          percentage: "14.9%",
          backgroundColor: "#fcf0e4",
          additionalValue: "(+43.21%)",
        },
        {
          title: "New Customers",
          value: "684",
          percentage: "- 8.6%",
          backgroundColor: "#edf5e8",
        },
        {
          title: "Purchase Rate",
          value: "75.12%",
          percentage: "25.4%",
          backgroundColor: "#eaf0fe",
          additionalValue: "(+20.11%)",
        },
        {
          title: "Average Value",
          value: "$2,412.23",
          percentage: "35.2%",
          backgroundColor: "#ecf5f4",
          additionalValue: "(+$754)",
        },
        {
          title: "Conversion Rate",
          value: "32.65%",
          percentage: "- 12.42%",
          backgroundColor: "#f6eced",
        },
        {
          title: "Average Order Value",
          value: "$320.75",
          percentage: "8.2%",
          backgroundColor: "#ede7f6",
          additionalValue: "(+5.60%)",
        },
      ],
      cardRows: [
        [{ component: "SummaryCard" }, { component: "ProductCard" }],
        [{ component: "RecentOrderCard" }, { component: "WeeklyCustomerCard" }],
      ],
    };
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
  grid-template-columns: repeat(6, 1fr);
  gap: 10px;
  width: 100%;
}

.card {
  padding: 10px 20px 0px 20px;
  border: 1px solid #ddd;
  border-radius: 12px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.05);
}

.cards-layout {
  margin-top: 10px;
}

.card-row {
  display: grid;
  grid-template-columns: 3fr 2fr;
  margin-bottom: 10px;
  gap: 10px;
}

@media (max-width: 1400px) {
  .stat-cards {
    grid-template-columns: repeat(3, 1fr);
  }
}
@media (max-width: 1200px) {
  .card-row {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 900px) {
  .stat-cards {
    grid-template-columns: repeat(2, 1fr);
  }

  .card-row {
    grid-template-columns: 1fr;
    margin-bottom: 10px;
  }
}

@media (max-width: 700px) {
  .stat-cards {
    grid-template-columns: 1fr;
  }

  .card-row {
    grid-template-columns: 1fr;
    margin-bottom: 10px;
  }
}
</style>
