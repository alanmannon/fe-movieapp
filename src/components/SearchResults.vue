<template>
  <div>
    <img :src=result.picture :alt=result.title>
    <router-link :to='`/show?id=${result.imdb}`'>
      <h2>{{result.title}}</h2>
    </router-link>
    <h2>Year: {{result.year}}</h2>
    <br>
  </div>
</template>

<script>
export default {
  name: "SearchResults",
  props: ["result"],
};
</script>

<style scoped>
</style>