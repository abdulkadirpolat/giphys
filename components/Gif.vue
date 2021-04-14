<template>
  <!-- <div class="image">
    <img :src="gif.images.fixed_height.url" />
  </div> -->
<!-- <div>{{gif}}</div> -->
  <!-- <div
    class="image"
    :style="`background-image:url(${gif.images.original.url})`"
  ></div> -->
  <img class="image" :src="`${gif.images.original.url}`" alt="">
</template>

<script>
// export default {
//   props: ['gif'],
// };
export default {
  name: "Gif",
  props: {
    gif: Object
  }
};
</script>

<style scoped lang="postcss">
/* .image {
  width: auto;
  height: 100%;
  transition: 300ms all;
}
.image img {
  border-radius: 10px;
  width: 100%;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
}

.image:hover {
  transform: scale(1.3);
} */
.image{
  @apply w-60 h-60 bg-no-repeat bg-cover bg-center
}
</style>
