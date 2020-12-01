<template>
  <div>
    <div :key="movie.title" v-for="movie in movies">
    <MovieItem :movie='movie' />
    </div>
  </div>
</template>

<script>
import MovieItem from "./MovieItem.vue";

export default {
  name: "Movies",
  components: {
    MovieItem,
  },
  props: ["movies"],
};
</script>

<style scoped>
</style>