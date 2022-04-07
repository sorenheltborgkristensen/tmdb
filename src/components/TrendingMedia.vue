<template>
  <section v-for="(trend, index) in trending" :key="index">
    <h2>{{ trend.title }}</h2>
    <img :src="'https://image.tmdb.org/t/p/w300/' + trend.poster_path" />
  </section>
</template>

<script>
export default {
  data() {
    return {
      trending: [],
    };
  },

  created() {
    this.getTrendingMedia();
  },

  methods: {
    async getTrendingMedia() {
      const url = `${"https://api.themoviedb.org/3/trending/movie/week?api_key=" + import.meta.env.VITE_API_KEY}`;
      const data = await (await fetch(url)).json();
      this.trending = data.results;
    },
  },
};
</script>
