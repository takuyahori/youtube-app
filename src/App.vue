<template>
  <div id="app">
    <header>
      <nav>
        <div class="navLeft">
          <img alt="" src="./assets/captain-american-4551118_1280.png">
        </div>
        <div class="navRight">
          <router-link to="/">Home</router-link>
          <router-link to="/video">Search Video</router-link>
        </div>
      </nav>
    </header>
    <router-view/>
  </div>
</template>

<script>
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}

header {
  background: rgb(35, 9, 115);
  width: 100%;
  height: 90px;
  z-index: 10;
  opacity: 0.8;
  font-weight: bold;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 100px 0 0;
}

nav a {
  font-weight: bold;
  color: rgb(255, 255, 255);
  text-decoration: none;
  font-size: 30px;
}

nav a:first-child {
  padding-right: 10px;
}

nav a:nth-child(2) {
  border-left: 1px solid #fff;
  padding-left: 10px;
}

nav a:hover {
  color: rgb(86, 198, 238);
  border-bottom: 1px solid rgb(86, 198, 238);
  padding-bottom: 8px;
}

.navLeft {
  width: 70px;
  height: 70px;
  margin-left: 80px;
}


.navLeft img {
  width: 100%;
  height: 100%;
}

@media screen and (max-width: 768px) {
  nav a {
    font-size: 20px;
  }

  .navLeft {
    margin-left: 30px;
  }

  .navRight {
    margin-right: -60px;
  }
}

</style>
