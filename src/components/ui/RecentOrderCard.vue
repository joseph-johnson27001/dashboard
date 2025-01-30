<template>
  <div class="recent-orders-card">
    <!-- Header Section -->
    <div class="header">
      <h3 class="title">Recent Orders</h3>
      <button class="view-all-button">View All</button>
    </div>

    <!-- Divider -->
    <div class="divider"></div>

    <!-- Table Section -->
    <table class="orders-table">
      <thead>
        <tr>
          <th>Product</th>
          <th>Customer</th>
          <th>ID</th>
          <th>Date</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(order, index) in orders" :key="index">
          <!-- Product with image -->
          <td class="product">
            <div class="product-info">
              <img :src="order.image" alt="Product" class="product-image" />
              <span class="product-name">{{ order.product }}</span>
            </div>
          </td>

          <!-- Customer Name -->
          <td>
            <span class="customer-name">{{ order.customer }}</span>
          </td>

          <!-- Order ID -->
          <td class="order-id">#{{ order.orderId }}</td>

          <!-- Date -->
          <td class="order-date">{{ order.date }}</td>

          <!-- Status -->
          <td>
            <span class="status-tag" :class="statusClass(order.status)">
              {{ order.status }}
            </span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "RecentOrderCard",
  data() {
    return {
      orders: [
        {
          product: "Smartphone",
          image: "images/items/Smartphone.jpg",
          customer: "Alice Johnson",
          orderId: "2345",
          date: "27/06/2025",
          status: "Pending",
        },
        {
          product: "Laptop",
          image: "images/items/laptop.png",
          customer: "Michael Smith",
          orderId: "6789",
          date: "25/06/2025",
          status: "Cancelled",
        },
        {
          product: "Gaming Mouse",
          image: "images/items/GamingMouse.png",
          customer: "Samantha Lee",
          orderId: "3456",
          date: "22/06/2025",
          status: "Shipped",
        },
      ],
    };
  },
  methods: {
    statusClass(status) {
      return {
        pending: status === "Pending",
        cancelled: status === "Cancelled",
        shipped: status === "Shipped",
      };
    },
  },
};
</script>

<style scoped>
/* Card Styling */
.recent-orders-card {
  padding: 20px 20px 0px 20px;
  border: 1px solid #eee;
  border-radius: 12px;
  background-color: white;
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

.view-all-button {
  background: none;
  border: 1px solid #eee;
  border-radius: 8px;
  color: #007bff;
  font-size: 14px;
  cursor: pointer;
  padding: 10px 15px;
}

/* Divider */
.divider {
  height: 1px;
  background-color: #eee;
  margin: 10px 0;
}

/* Table */
.orders-table {
  width: 100%;
  border-collapse: collapse;
}

.orders-table th {
  text-align: left;
  font-size: 14px;
  font-weight: bold;
  color: #333;
  padding-bottom: 10px;
}

.orders-table td {
  padding: 10px 0;
  font-size: 14px;
  color: #555;
}

/* Product Image & Name */
.product-info {
  display: flex;
  align-items: center;
}

.product-image {
  width: 50px;
  height: 50px;
  border-radius: 8px;
  margin-right: 10px;
}

.product-name {
  font-weight: 500;
}

/* Customer Name */
.customer-name {
  color: #007bff;
  cursor: pointer;
}

/* Order ID */
.order-id {
  color: #333;
  font-weight: 500;
}

/* Order Date */
.order-date {
  color: #777;
}

/* Status Tags */
.status-tag {
  padding: 5px 10px;
  border-radius: 12px;
  font-size: 13px;
  font-weight: 500;
}

/* Status Colors */
.pending {
  background-color: #fff3cd;
  color: #856404;
}

.cancelled {
  background-color: #f8d7da;
  color: #721c24;
}

.shipped {
  background-color: #d4edda;
  color: #155724;
}
</style>
