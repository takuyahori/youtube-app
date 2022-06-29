<template>
  <div class="home">
    <img alt="" src="../assets/iron-man-4228269_1920.jpg">
    <div class="homeTitle">
      <h1>The Marvel information</h1>
    </div>
  </div>
</template>

<script>

</script>

<style>

.home {
  position: relative;
}

img {
  width: 100%;
  height: 100vh;
}

.homeTitle {
  width: 600px;
  margin: -400px auto 0;
  color: rgb(237, 237, 237);
  font-size: 4vh;
  text-shadow: 5px 3px 4px rgb(35, 9, 115);
}

@media screen and (max-width: 768px) {
  .homeTitle {
    width: 300px;
  }
}

</style>
