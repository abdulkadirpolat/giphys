<template>
  <!-- <div class=" mx-auto max-w-8xl ">
    <Search @SearchRequested="search"></Search>
    <transition name="fade">
      <div v-if="gifs.length > 0" class="container">
        <Gif v-for="gif in gifs" :gif="gif" :key="gif.id"></Gif>
      </div>
      <div class="loading" v-else>
        <h1 class="text">Loading...</h1>
      </div>
    </transition>
  </div> -->
  <div class="mx-auto max-w-8xl">
    <!-- <search @fetch-gifts='onFetch' />
    <gif-list :gifs="gifs" /> -->
    <Search  @fetch-gifts='onFetch'></Search>
    <GifList :gifs="gifs"></GifList>
  </div>
</template>

<script>
// import Axios from "axios";

export default {
  name:'index',
  data() {
    return {
      gifs: []
    };
  },
  methods:{
onFetch(result) {
  this.gifs = result
}
  }

  // async asyncData() {
  //   try {
  //     const api = `https://api.giphy.com/v1/gifs/trending?api_key=${process.env.VUE_APP_API_KEY}`;
  //     const gifs = await Axios.get(api).then(response => {
  //       return console.log(response.data);
  //     });

  //     return { gifs };
  //   } catch (error) {
  //     return { error };
  //   }
  // }
  // data() {
  //   return {
  //     gifs: []
  //   };
  // },
  // methods: {
  //   async getReq(url) {
  //     if (!url) return;
  //     const res = await Axios.get(url);
  //     const data = await res.data.data;
  //     return data;
  //   },
  //   trend() {
  //     this.getReq(
  //       `https://api.giphy.com/v1/gifs/trending?api_key=${process.env.VUE_APP_API_KEY}`
  //     )
  //       .then(data => {
  //         this.gifs = data;
  //       })
  //       .catch(err => console.warn(err));
  //   },
  //   search(searchQuery) {
  //     if (!searchQuery) {
  //       this.trend();
  //     } else {
  //       this.gifs = [];
  //       this.getReq(
  //         `https://api.giphy.com/v1/gifs/search?api_key=${process.env.VUE_APP_API_KEY}&q=${searchQuery}`
  //       )
  //         .then(data => {
  //           this.gifs = data;
  //         })
  //         .catch(err => console.warn(err));
  //     }
  //   }
  // },
  // watch: {
  //   gifs() {
  //     console.log(this.gifs);
  //   }
  // },

  // created() {
  //   this.trend();
  // }
};
</script>

<style scoped lang="postcss">
.container {
  /* display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  margin-top: 10px;
  margin-bottom: 50px; */
  @apply flex flex-wrap justify-evenly mt-3 mb-12;
}

.container .image {
  @apply m-1;
}

.loading {
  /* margin-top: 50px;
  display: flex;
  align-items: center;
  justify-content: center; */
  @apply mt-12 flex items-center justify-center;
}
.loading .text {
  /* color: #fff;
  background: #222;
  width: fit-content;
  padding: 10px 20px;
  border-radius: 10px; */
  @apply text-white bg-gray-800 w-80 py-3 px-5 rounded-xl;
}

.fade-enter-active,
.fade-leave-active {
  /* transition: opacity 0.5s;
   */
  @apply transition-opacity opacity-50;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  /* opacity: 0; */
  @apply opacity-0;
}
</style>
