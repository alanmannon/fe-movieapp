<template>
  <div class="show">
    <img :src="movie.image" />
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
      downCount: [],
    };
  },

  created: function () {
    this.getMovie();
    // this.dbCheck();
  },

  methods: {
    getMovie: function () {
      axios.get("/api/search/" + this.$route.query.id).then((response) => {
        this.movie = response.data;
      });
    },
    dbCheck: function () {
      axios.post("/api/movies/?imdb=" + this.$route.query.id, {
        params: {
          title: this.movie.title,
          year: this.movie.year,
          image: this.movie.poster,
          imdb: this.movie.imdbID,
        },
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
        });
    },
    thumbsDown: function () {
      this.downCount = this.movie.thumbs_down + 1;
      axios
        .patch(
          "/api/movies/" +
            this.$route.query.id +
            "?thumb=0&new=" +
            this.downCount
        )
        .then((response) => {
          this.movie.thumbs_down = response.data["thumbs_down"];
        });
    },
  },
};
</script>


<style scoped>
</style>