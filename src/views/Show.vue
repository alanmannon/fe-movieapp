<template>
  <div class="show">
    <h1>{{ movie.title }}</h1>
    <h4>({{ movie.year }})</h4>
    <h3>Directed by: {{ movie.director }}</h3>
    <p>{{ movie.description }}</p>
    <h2><a @click.prevent="thumbsUp()">Thumbs Up:</a> {{ movie.thumbs_up }}</h2>
    <h2><a @click.prevent="thumbsDown()">Thumbs Down:</a> {{ movie.thumbs_down }}</h2>
  </div>  
</template>

<script>
import axios from "axios";

export default {
  name: "Show",
  data: function () {
    return {
      movie: [],
      upCount: [],
    };
  },

  created: function () {
    this.getMovie();
  },

  methods: {
    getMovie: function () {
      axios.get("/api/search" + this.$route.query.id).then((response) => {
        this.movie = response.data;
      });
    },
    thumbsUp: function () {
      this.upCount = this.movie.thumbs_up + 1;
      axios
        .patch(
          "/api/movies/" + this.$route.query.id + "?thumb=1&new=" + this.upCount
        )
        .then((response) => {
          this.movie.thumbs_up = response.data["thumbs_up"];
          console.log(response.data);
        });
    },
    thumbsDown: function () {
      this.movie.thumbs_down += 1;
      axios
        .patch("/api/movies/?" + this.$route.query.id + "&thumb=0")
        .then((response) => {
          this.movie = response.data;
        });
    },
  },
};
</script>


<style scoped>
</style>