<template>
  <div class="product-card">
    <!-- Top Heading Section -->
    <div class="header">
      <h3 class="title">Most Selling Products</h3>
      <span class="three-dots">
        <i class="fas fa-ellipsis"></i>
      </span>
    </div>

    <!-- Divider -->
    <div class="divider"></div>

    <div class="items">
      <div class="item-row" v-for="(item, index) in items" :key="index">
        <div
          class="item-image"
          :style="{ backgroundImage: `url(${item.image})` }"
        ></div>

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
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0;
}

.title {
  font-size: 16px;
  font-weight: 400;
  color: #15161b;
  margin-right: 8px;
}

.three-dots i {
  font-size: 14px;
  color: grey;
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
  border-bottom: 1px solid #eee;
  padding: 10px 0;
  cursor: pointer;
}

.item-row:last-child {
  border-bottom: none;
}

.item-image {
  width: 55px;
  height: 55px;
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
  font-size: 14px;
  font-weight: 400;
  color: #15161b;
  margin: 0;
  cursor: pointer;
}

.item-id {
  font-size: 12px;
  color: #888;
  margin-top: 0;
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

@media (max-width: 350px) {
  .header {
    margin-bottom: 8px;
  }

  .title {
    font-size: 13px;
  }

  .divider {
    margin-top: 4px;
  }

  .item-row {
    align-items: center;
    padding: 10px 0;
  }

  .item-name {
    font-size: 12px !important;
  }

  .item-image {
    width: 45px;
    height: 45px;
    margin-right: 8px;
  }

  .item-details {
    margin-left: 8px;
  }

  .sales-container {
    text-align: center;
  }

  .sales-count {
    font-size: 11px;
  }
}

@media (max-width: 265px) {
  .item-row {
    justify-content: space-between;
  }

  .sales-container {
    display: flex;
    padding: 15px;
  }

  .item-image {
    height: 35px;
    width: 35px;
  }
}
</style>
