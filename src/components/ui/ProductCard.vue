<template>
  <div class="product-card">
    <!-- Top Heading Section -->
    <div class="header">
      <h3 class="title">Most Selling Products</h3>
      <span class="three-dots">...</span>
    </div>

    <!-- Divider -->
    <div class="divider"></div>

    <!-- Rows of Items -->
    <div class="items">
      <!-- Loop through products using v-for -->
      <div class="item-row" v-for="(item, index) in items" :key="index">
        <div
          class="item-image"
          :style="{ backgroundImage: `url(${item.image})` }"
        ></div>

        <!-- Placeholder for image -->
        <div class="item-details">
          <h4 class="item-name">{{ item.name }}</h4>
          <p class="item-id">ID: {{ item.id }}</p>
        </div>
        <div class="sales-container">
          <span class="sales-count">{{ item.sales }} sales</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  data() {
    return {
      items: [
        {
          name: "Gaming Mouse",
          id: 12345,
          sales: 128,
          image: "images/items/GamingMouse.png",
        },
        {
          name: "Smart Phone",
          id: 12346,
          sales: 142,
          image: "images/items/Smartphone.jpg",
        },
        {
          name: "Headphones",
          id: 12347,
          sales: 150,
          image: "images/items/Headphones.png",
        },
        {
          name: "Laptop",
          id: 12347,
          sales: 150,
          image: "images/items/laptop.png",
        },
      ],
    };
  },
};
</script>

<style scoped>
.product-card {
  padding: 20px 20px 0px 20px;
  border: 1px solid #eee;
  border-radius: 12px;
  background-color: white;
}

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

.three-dots {
  font-size: 30px;
  color: grey;
  cursor: pointer;
}

.divider {
  height: 1px;
  background-color: #eee;
  margin: 10px 0;
}

.items {
  display: flex;
  flex-direction: column;
}

.item-row {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
}

.item-image {
  width: 60px;
  height: 60px;
  border-radius: 8px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  cursor: pointer;
  margin-right: 15px;
}

.item-details {
  flex-grow: 1;
}

.item-name {
  font-size: 16px;
  font-weight: 400;
  color: #15161b;
  margin: 0;
  cursor: pointer;
}

.item-id {
  font-size: 12px;
  color: #888;
  margin-top: 0px;
}

.sales-container {
  padding: 5px 10px;
  border-radius: 8px;
  border: 1px solid #ddd;
  cursor: pointer;
}

.sales-count {
  font-size: 14px;
  color: #333;
}
</style>
