<template>
  <div class="navbar">
    <!-- Left: Search Bar -->
    <div class="search-bar">
      <i class="fas fa-search"></i>
      <input type="text" placeholder="Search" />
    </div>

    <!-- Right: Profile and Icons -->
    <div class="user-icons">
      <div class="icon-circle"><span>文</span></div>
      <!-- Language icon -->
      <div class="icon-circle"><i class="fa fa-check"></i></div>
      <!-- Scan icon -->
      <div class="icon-circle"><i class="far fa-star"></i></div>
      <!-- Moon icon -->
      <div class="icon-circle"><i class="fa fa-alt fa-map-pin"></i></div>
      <!-- Pin icon -->
      <div class="profile-circle">
        <img src="profile.jpg" alt="Profile" />
        <!-- Profile Image -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #555;
  width: 100%;
  border-bottom: 1px solid #eee;
  padding: 5px 0px;
}

.search-bar {
  display: flex;
  align-items: center;
  background-color: #f4f7fe;
  padding: 10px 15px;
  margin: 10px 20px;
  width: 30%;
  border-radius: 10px;
  font-size: 16px;
  border: 1px solid #eee;
  cursor: text;
}

.search-bar i {
  margin-right: 10px;
  font-size: 12px;
}

.search-bar input {
  width: 100%;
  border: none;
  background: transparent;
  font-size: 14px;
  outline: none;
  font-family: "Poppins", sans-serif;
}

.search-bar input::placeholder {
  color: #555;
}

.user-icons {
  display: flex;
  align-items: center;
  margin: 10px 40px;
  cursor: pointer;
}

.icon-circle {
  width: 35px;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 50%;
  margin-left: 10px;
  font-size: 12px;
  border: 1px solid #ccc;
  color: #555;
}

.profile-circle {
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 50%;
  border: 1px solid #ccc;
  margin-left: 15px;
}

.profile-circle img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}
</style>
