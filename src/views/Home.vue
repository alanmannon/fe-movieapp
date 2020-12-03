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
      rawMovies: [],
    };
  },

  created: function () {
    this.movieIndex();
  },

  methods: {
    movieIndex: function () {
      axios.get("/api/movies").then((response) => {
        this.rawMovies = response.data;
        this.movies = this.sortedMovies(this.rawMovies);
      });
    },
    sortedMovies: function () {
      return this.rawMovies.sort((a, b) => b.thumbs_up - a.thumbs_up);
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
