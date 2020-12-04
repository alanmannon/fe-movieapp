<template>
  <div class="movie-item">
    <img :src="movie.picture" :alt=movie.title>
    <router-link :to='`/show?id=${movie.imdb}`'>
      <h2>{{movie.title}}</h2>
    </router-link>
    <h4 class="year">({{movie.year}})</h4>
    <h2>Thumbs Up: {{movie.thumbs_up}}</h2>
    <h2>Thumbs Down: {{movie.thumbs_down}}</h2>



<!-- <table class="table table-striped">
  <thead>
    <tr>
      <th>Author</th>
      <th>Title</th>
    </tr>
  </thead>
  <tbody>         
    {{#each movie}}
      <tr>
        <td>{{author}}</td> 
        <td>{{title}}</td>       
      </tr>
    {{/each}}       
  </tbody>
</table> -->


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
.year {
  font-style: italic;
}
</style>