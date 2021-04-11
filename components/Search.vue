<template>
  <div class="search-nav">
    <!-- @keydown="searchRequested" -->
    <!-- v-model="searchQuery" -->
    <input
      type="text"
      @input="onInput"
      v-model="keyword"
      class="search-input"
      placeholder="search gif."
    />
  </div>
</template>

<script>
export default {
  name:'Search',
  data(){
    return{
      keyword="",
      timeout=null,
    }
  },
  methods: {
    onInput(){
clearTimeout(this.timeout);
 this.timeout= setTimeout(()=>{
   this.search()

 })

    },
    search(){
       fetch(`https://api.giphy.com/v1/gifs/search?api_key=j2VzG5q20cDSUMeZ4sDBxcEyoXyATC2v
&q=${this.keyword}`)
.then(response => response.json())
.then(result => {
  console.log(result);
  this.gifs = result.data;
  this.$$emit('fetch-gifs',result.data)
})
    }
  }
  // data() {
  //   return {
  //     searchQuery: ""
  //   };
  // },
  // methods: {
  //   searchRequested() {
  //     this.$emit("SearchRequested", this.searchQuery);
  //   }
  // }
};
</script>

<style scoped lang="postcss">
.search-nav {
  background: #fff;
  @apply sticky top-0 w-full h-16 flex items-center justify-center py-3 px-12 shadow-md;
}

.search-input {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  @apply font-bold h-full w-full max-w-sm text-2xl text-center rounded-md outline-none    border-2 border-opacity-70 border-gray-300   focus:border-transparent   focus:ring-2 focus:ring-purple-300 placeholder-gray-300;
}
</style>
