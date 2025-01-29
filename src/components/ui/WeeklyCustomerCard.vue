<template>
  <div class="recent-orders-card">
    <!-- Top Heading Section -->
    <div class="header">
      <h3 class="title">Weekly Top Customers</h3>
      <span class="three-dots">...</span>
    </div>

    <!-- Rows of Customers -->
    <div class="customers">
      <div
        class="customer-row"
        v-for="(customer, index) in customers"
        :key="index"
      >
        <div
          class="profile-image"
          :style="{ backgroundImage: `url(${customer.image})` }"
        ></div>
        <div class="customer-details">
          <h4 class="customer-name">{{ customer.name }}</h4>
          <p class="order-count">{{ customer.orders }} orders</p>
        </div>
        <button class="view-button">View</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WeeklyCustomersCard",
  data() {
    return {
      customers: [
        {
          name: "Alice Johnson",
          orders: 25,
          image: "https://via.placeholder.com/50", // Placeholder image
        },
        {
          name: "Michael Smith",
          orders: 18,
          image: "https://via.placeholder.com/50",
        },
        {
          name: "Samantha Lee",
          orders: 30,
          image: "https://via.placeholder.com/50",
        },
      ],
    };
  },
};
</script>

<style scoped>
.recent-orders-card {
  padding: 0px 20px;
  border: 1px solid #eee;
  border-radius: 12px;
  background-color: white;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5px;
}

.title {
  font-size: 16px;
  font-weight: bold;
  color: black;
}

.three-dots {
  font-size: 30px;
  color: grey;
  cursor: pointer;
}

.customers {
  display: flex;
  flex-direction: column;
}

.customer-row {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
}

.profile-image {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-size: cover;
  background-position: center;
  margin-right: 15px;
  border: 1px solid #eee;
  background-color: #e0e0e0;
  cursor: pointer;
}

.customer-details {
  flex-grow: 1;
}

.customer-name {
  font-size: 16px;
  font-weight: 400;
  color: black;
  cursor: pointer;
  margin: 0;
}

.order-count {
  font-size: 12px;
  color: #888;
  margin-top: 0px;
}

.view-button {
  padding: 10px 12px;
  border: none;
  border-radius: 8px;
  color: #007bff;
  background-color: white;
  cursor: pointer;
  font-size: 14px;
  border: 1px solid #eee;
}
</style>
