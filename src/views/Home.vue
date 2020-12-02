<template>
  <div id="home">
    <Movies :movies="movies"/>
  </div>
</template>

<script>
import axios from "axios";
import Movies from "../components/Movies";

export default {
  name: "Home",
  components: {
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
        console.log(this.movies);
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
