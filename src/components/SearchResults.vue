<template>
  <div>
    <img :src=result.image :alt=result.title>
    <h2>{{result.title}}</h2>
    <h2>Year: {{result.year}}</h2>
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