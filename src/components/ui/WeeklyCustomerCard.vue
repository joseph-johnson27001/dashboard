<template>
  <div class="weekly-orders-card">
    <div class="header">
      <h3 class="title">Weekly Top Customers</h3>
      <span class="three-dots">
        <i class="fas fa-ellipsis"></i>
      </span>
    </div>

    <div class="divider"></div>

    <div class="customers">
      <div
        class="customer-row"
        v-for="(customer, index) in customers"
        :key="index"
      >
        <div style="display: flex; flex-direction: row">
          <div
            class="profile-image"
            :style="{ backgroundImage: `url(${customer.image})` }"
          ></div>
          <div class="customer-details">
            <h4 class="customer-name">{{ customer.name }}</h4>
            <p class="order-count">{{ customer.orders }} orders</p>
          </div>
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
          image: "/images/ProfilePhoto1.jpg",
        },
        {
          name: "Michael Smith",
          orders: 18,
          image: "/images/ProfilePhoto4.jpg",
        },
        {
          name: "Samantha Lee",
          orders: 30,
          image: "/images/ProfilePhoto3.jpg",
        },
        {
          name: "Charlotte Colton",
          orders: 32,
          image: "/images/ProfilePhoto2.jpg",
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
  flex-wrap: wrap;
}

.title {
  font-size: 16px;
  font-weight: 400;
  color: #15161b;
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

.customers {
  display: flex;
  flex-direction: column;
  padding-top: 8px;
}

.customer-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 15px;
  width: 100%;
  justify-content: space-between;
}

.profile-image {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  background-size: cover;
  background-position: center;
  margin-right: 15px;
  border: 1px solid #eee;
  background-color: #e0e0e0;
  cursor: pointer;
  flex-shrink: 0;
}

.customer-name {
  font-size: 16px;
  font-weight: 400;
  color: #15161b;
  cursor: pointer;
  margin: 0;
  white-space: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  flex-grow: 1;
}

.order-count {
  font-size: 12px;
  color: #888;
  margin-top: 0;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.view-button {
  padding: 8px 12px;
  border: none;
  border-radius: 8px;
  color: #007bff;
  background-color: white;
  cursor: pointer;
  font-size: 14px;
  border: 1px solid #eee;
  margin-left: 10px;
}

.customer-row {
  cursor: pointer;
}

@media (max-width: 350px) {
  .customer-row {
    align-items: flex-start;
  }

  .profile-image {
    width: 35px;
    height: 35px;
    margin-bottom: 8px;
  }

  .customer-name {
    font-size: 13px;
  }

  .order-count {
    font-size: 10px;
  }

  .view-button {
    padding: 5px 8px;
    font-size: 11px;
  }
}
</style>
