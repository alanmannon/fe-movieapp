<template>
  <div>
    <h1>Search for your favorite movies!</h1>
    <input type="text" v-model="search" @keyup.enter="$emit('movieSearch', search)">
    <button type="button" v-on:click="$emit('movieSearch', search)" >
      Search
    </button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  components: {},

  data: function () {
    return {
      search: "",
    };
  },
};
</script>