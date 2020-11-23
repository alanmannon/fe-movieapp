<template>
  <div id="app">
    <Header />
    <Movies v-bind:movies="movies"/>
  </div>
</template>

<script>
import axios from "axios";
import Movies from "./components/Movies";
import Header from "./components/layout/Header";
export default {
  name: "App",
  components: {
    Header,
    Movies,
  },
  data: function () {
    return {
      movies: [],
    };
  },
  created: function () {
    this.movieIndex();
  },
  methods: {
    movieIndex: function () {
      axios.get("/api/movies").then((response) => {
        this.movies = response.data;
      });
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
