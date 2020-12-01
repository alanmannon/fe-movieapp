<template>
  <div class="search">
    <SearchBar @movieSearch="movieSearch"/>
    <SearchResults 
      :key="result.id"
      v-for="result in results"
      :result='result' 
    />
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "../components/SearchBar.vue";
import SearchResults from "../components/SearchResults.vue";
export default {
  name: "Search",
  data: function () {
    return {
      results: [],
      error: [],
    };
  },
  components: {
    SearchBar,
    SearchResults,
  },
  methods: {
    movieSearch: function (search) {
      axios
        .get("/api/search/", {
          params: {
            search: search,
          },
        })
        .then((response) => {
          this.results = response.data;
          console.log(this.results);
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
      console.log(search);
    },
  },
};
</script>