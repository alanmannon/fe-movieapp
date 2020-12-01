<template>
  <div>
    <h1>Search for your favorite movies!</h1>
    <input type="text" v-model="search">
    <button type="button" v-on:click="$emit('movieSearch', search)" >
      Search
    </button>
     <!-- <div v-bind:key="result.title" v-for="result in results">
    <SearchResults :result='result' />
    </div> -->
  </div>
</template>

<script>
// import SearchResults from "./SearchResults.vue";

export default {
  name: "SearchBar",
  components: {
    // SearchResults,
  },

  data: function () {
    return {
      search: "",
    };
  },
};
</script>