<template>
  <div class="search">
    <h1>Search for your favorite movies!</h1>
    <input type="text" v-model="search">
    <button type="button" v-on:click="movieSearch()" >
      Search
    </button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      search: "",
    };
  },
  methods: {
    movieSearch: function () {
      var params = {
        search: this.search,
      };

      axios.get("/api/search", params).then((response) => {
        console.log(response.data);
      });
    },
  },
};
</script>