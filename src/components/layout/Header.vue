<template>
  <header class="header">
    <h1>Movie App</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/search">Search</router-link>
    </div>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>
.header {
  /* display: flex; */
  /* top: 0; */
  width: 100%;
  padding: 5px;
  /* height: 8rem; */
  /* background-color: rgb(184, 17, 17); */
  /* box-shadow: 0 10px 30px 4px rgba(0, 0, 0, 0.351); */
  align-items: center;
}
</style>