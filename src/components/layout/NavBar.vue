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
        <img src="/images/ProfilePhoto3.jpg" alt="Profile" />
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
  border-bottom: 1px solid #ccc;
  background-color: #eaf0fe;
}

.search-bar {
  display: flex;
  align-items: center;
  background-color: #fff;
  padding: 5px 10px;
  margin: 10px 20px;
  width: 30%;
  border-radius: 4px;
  font-size: 16px;
  border: 1px solid #ccc;
  cursor: text;
}

.search-bar i {
  margin-right: 2px;
  font-size: 12px;
}

.search-bar input {
  width: 100%;
  border: none;
  background: transparent;
  font-size: 14px;
  height: 100%;
  outline: none;
  font-family: "Poppins", sans-serif;
}

.search-bar input::placeholder {
  color: #444;
}

.search-bar:focus-within {
  border-color: #64b5f6;
  box-shadow: 0 0 3px rgba(100, 181, 246, 0.75);
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
  margin-left: 10px;
  font-size: 12px;
  border: 1px solid #aaa;
  color: #15161b;
}

.profile-circle {
  width: 35px;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 50%;
  border: 1px solid #aaa;
  margin-left: 15px;
}

.profile-circle img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

@media (max-width: 550px) {
  .icon-circle {
    display: none;
  }
  .search-bar {
    flex-grow: 1;
    margin: 5px;
  }
  .profile-circle {
    margin: 0px;
  }
  .user-icons {
    margin-left: 10px;
    margin-right: 10px;
  }
}
</style>
