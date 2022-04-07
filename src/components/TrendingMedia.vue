<template>
  <section v-for="(trend, index) in trending" :key="index">
    {{ trend.title }}
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
      const url = `${"https://api.themoviedb.org/3/trending/all/week?api_key=" + import.meta.env.VITE_API_KEY}`;
      const data = await (await fetch(url)).json();
      this.trending = data.results;
    },
  },
};
</script>
