<template>
  <div class="movie-item">
    <img v-bind:src="movie.image" alt="poster"/>
    <h2>{{movie.title}}</h2>
    <h2>{{movie.year}}</h2>
  </div>
</template>

<script>
export default {
  name: "MovieItem",
  props: ["movie"],
};
</script>

<style scoped>
.movie-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
</style>