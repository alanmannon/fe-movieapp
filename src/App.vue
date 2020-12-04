<template>
  <div id="app">
    <div id="nav">
      <Header />
    </div>
    <router-view/>
  </div>
</template>

<script>
import Header from "./components/layout/Header";
export default {
  name: "app",
  components: {
    Header,
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  font-weight: bold;
  color: #2c3e50;
  background-color: rgb(184, 17, 17);
}

#nav a {
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
