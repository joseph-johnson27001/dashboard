<template>
  <div class="navbar">
    <!-- Left: Search Bar -->
    <div class="search-bar">
      <i class="fas fa-search"></i>
      <span>Search</span>
    </div>

    <!-- Right: Profile and Icons -->
    <div class="user-icons">
      <div class="icon-circle"><span>文</span></div>
      <!-- Language icon -->
      <div class="icon-circle"><i class="fas fa-qrcode"></i></div>
      <!-- Scan icon -->
      <div class="icon-circle"><i class="fas fa-moon"></i></div>
      <!-- Moon icon -->
      <div class="icon-circle"><i class="fas fa-map-pin"></i></div>
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
}

.search-bar {
  display: flex;
  align-items: center;
  background-color: #f4f7fe;
  padding: 10px 15px;
  margin: 10px;
  width: 40%;
  border-radius: 10px;
  font-size: 16px;
  border: 1px solid #eee;
  cursor: text;
}

.search-bar i {
  margin-right: 10px;
  font-size: 12px;
}

.search-bar span {
  font-size: 12px;
  font-weight: 100;
}

.user-icons {
  display: flex;
  align-items: center;
  margin: 10px 20px;
  cursor: pointer;
}

.icon-circle {
  width: 25px;
  height: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 50%;
  margin-left: 15px;
  font-size: 12px;
  border: 1px solid #ccc;
}

.profile-circle {
  width: 35px;
  height: 35px;
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
