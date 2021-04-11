<template>
  <div class="gifList">
    <gif v-for="gif in gifs" :key="gif.id" :gif="gif" />
  </div>
</template>
<script>
export default {
  name: "GifList",
  props: {
    gifs: Array
  }
};
</script>
<style lang="postcss" scoped>
.gifList {
  @apply flex flex-wrap justify-evenly mt-3 mb-12;
}
.container .image {
  @apply m-1;
}
</style>
