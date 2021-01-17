<template>
  <div id="app">
    <SearchBar @search-query="handleSearchedQuery" />
    <div v-if="Loading" class="spinner-border text-danger" role="status">
      <span class="sr-only">Loading...</span>
    </div>
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <Gifs v-bind:gifs="gifs" />
  </div>
</template>

<script>
import Gifs from "./components/Gifs.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
  name: "App",
  components: {
    Gifs,
    SearchBar,
  },
  data() {
    return {
      gifs: [],
      Loading: true,
    };
  },
  methods: {
    fetchProcess(url) {
      fetch(url)
        .then((res) => res.json())
        .then((res) => {
          this.gifs = res.data;
          this.Loading = false;
          res.data.forEach(data=>console.log(data))
        });
        
    },
    handleSearchedQuery(searchQuery) {
      this.gifs = [];
      this.Loading = true;
      let url = `http://api.giphy.com/v1/gifs/search?q=${searchQuery}&api_key=56rwU5fyzUX0VjAp1s9BPa3It7MSRdoT`;
      this.fetchProcess(url);
      
    },
  },
  created() {
    let url ="http://api.giphy.com/v1/gifs/trending?api_key=56rwU5fyzUX0VjAp1s9BPa3It7MSRdoT";
    this.fetchProcess(url);
  
//Datanın içinde imageın içinde fixed_height içinde url'İ alıcaz
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
