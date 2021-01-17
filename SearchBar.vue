<template>
  <div class="search-bar">
      <h3 id="title">SEARCH GIFS</h3>
    <div class="input-group mb-3">
      <input
        v-model="searchQuery"
        @keypress.enter="handleQuery"
        type="text"
        class="form-control"
        aria-label="Default"
        aria-describedby="inputGroup-sizing-default"
      />
      
    </div>
    <button id="search-btn" @click="handleQuery" class="btn btn-primary">Search</button>
  </div>
</template>
<script>
export default {
  data(){
    return{
      searchQuery:""
    }
  },
  methods:{
    handleQuery(){
      //console.log(this.searchQuery);
      this.$emit("search-query",this.searchQuery);//search-query app'de karşılanacak name gibi düşün
    }
  }

};
</script>
<style scoped>
.form-control{
    margin-left: 10%;
    margin-right: 10%;
    margin-bottom: 500%;
}
.search-bar{
  background-color:#1DEA90;
}
#title{
  
}
</style>
