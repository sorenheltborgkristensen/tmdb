<template>
  <base-media-slider>
    <section class="media-slider-card" v-for="(trend, index) in trending" :key="index">
      <!-- Filmplakat -->
      <img :src="'https://image.tmdb.org/t/p/w220_and_h330_face/' + trend.poster_path" />
      <div>
        <!-- Bedømmelse -->
        <p class="average-score">{{ trend.vote_average }}</p>

        <!-- Titel -->
        <h2>{{ trend.title }}</h2>
        <h2 v-if="trend.media_type == 'tv'">{{ trend.name }}</h2>

        <!-- Udgivelsesdato -->
        <p class="release-date">{{ trend.release_date }}</p>
        <p v-if="trend.media_type == 'tv'" class="release-date">{{ trend.first_air_date }}</p>
      </div>
    </section>
  </base-media-slider>
</template>

<script>
import BaseMediaSlider from "./UI/BaseMediaSlider.vue";

export default {
  components: { BaseMediaSlider },

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
      try {
        const url = `${"https://api.themoviedb.org/3/trending/all/day?api_key=" + import.meta.env.VITE_API_KEY}`;
        const data = await (await fetch(url)).json();
        this.trending = data.results;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
.media-slider-card {
  margin-left: 40px;
}

.media-slider-card img {
  width: 150px;
  border-radius: 6px;
}

.media-slider-card div {
  position: relative;
  padding: 26px 10px 12px 10px;
}
.media-slider-card div .average-score {
  background-color: red;
  color: #ffffff;
  font-size: 12px;
  width: 34px;
  height: 34px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: -19px;
}

.media-slider-card div h2 {
  font-size: 16px;
}

.media-slider-card div .release-date {
  color: rgba(0, 0, 0, 0.6);
}
</style>
