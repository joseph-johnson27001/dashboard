<template>
  <div class="heading-area">
    <!-- Welcome text -->
    <div class="welcome-text">
      <h1>Welcome back, Joanne!</h1>
      <p>Here's what's happening with your store today</p>
    </div>

    <!-- Buttons -->
    <div class="buttons">
      <button class="previous-year">
        Previous Year <i class="fas fa-chevron-down"></i>
      </button>
      <button class="view-all-time">View All Time</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeadingArea",
};
</script>

<style scoped>
.heading-area {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  padding: 10px;
}

.welcome-text {
  flex-grow: 1;
}

.welcome-text h1 {
  font-size: 24px;
  font-weight: 400;
  margin: 0;
  color: #000;
}

.welcome-text p {
  font-size: 14px;
  color: #555;
  margin-top: 5px;
}

.buttons {
  display: flex;
  align-items: center;
}

button {
  padding: 15px 20px;
  margin-left: 10px;
  font-size: 14px;
  font-weight: 400;
  cursor: pointer;
  border-radius: 8px;
  display: flex;
  align-items: center;
}

.view-all-time {
  background-color: black;
  color: white;
  border: none;
}

.previous-year {
  background-color: white;
  color: #000;
  border: 1px solid #ccc;
}

.previous-year i {
  margin-left: 5px;
  color: #555;
}

button:hover {
  opacity: 0.8;
}
</style>
