<template>
  <div class="container">
    <Hero />
  </div>
</template>

<script>
import Hero from "../components/Hero.vue";
import axios from "axios";
export default {
  data() {
    return {
      Animek: [],
    };
  },
  async fetch() {
    await this.getTopAnime();
  },

  methods: {
    async getTopAnime() {
      const data = axios.get("https://api.jikan.moe/v4/top/anime");
      const result = await data;
      result.data.data.forEach((anime) => {
        this.Animek.push(anime);
      });
      console.log(this.Animek);
    },
  },

  name: "IndexPage",
  components: { Hero },
};
</script>
