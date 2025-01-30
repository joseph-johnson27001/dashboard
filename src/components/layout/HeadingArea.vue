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
}

.welcome-text {
  flex-grow: 1;
  margin-bottom: 0px;
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
  margin: 5px 0px 0px 0px;
}

.buttons {
  display: flex;
  align-items: center;
}

button {
  padding: 10px 20px;
  margin-left: 10px;
  font-size: 14px;
  font-weight: 400;
  cursor: pointer;
  border-radius: 8px;
  display: flex;
  align-items: center;
}

.view-all-time {
  background-color: #15161b;
  color: white;
  border: none;
}

.previous-year {
  background-color: white;
  color: #15161b;
  border: 1px solid #ccc;
}

.previous-year i {
  margin-left: 5px;
  color: #555;
}

button:hover {
  opacity: 0.8;
}

@media (max-width: 800px) {
  .heading-area {
    flex-direction: column;
    align-items: flex-start;
  }

  .buttons {
    margin-top: 15px;
    justify-content: flex-start;
    width: 100%;
  }

  button {
    margin-left: 0;
    margin-right: 10px;
  }
}
</style>
