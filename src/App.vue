<template>
  <trending-media></trending-media>
</template>

<script>
import TrendingMedia from "./components/TrendingMedia.vue";

export default {
  components: {
    TrendingMedia,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&display=swap");

* {
  margin: 0;
  padding: 0;
}

body {
  font-family: "Source Sans Pro", sans-serif;
  max-width: 1300px;
  margin: 0 auto;
}
</style>
