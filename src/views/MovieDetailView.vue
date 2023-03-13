<template>
  <!-- <div class="movie-detail">Detail : {{ $route.params.id }}</div> -->
  <div class="movie-detail">
    <h2>Movie Title : {{ movie.Title }}</h2>
    <p>{{ movie.Year }}</p>
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <p>{{ movie.Plot }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "@/env.js";
export default {
  name: "MovieDetailView",
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      console.log("onBeforeMount");
      fetch(
        `http://www.omdbapi.com/?i=tt3896198&apikey=${env.apiKeys}&id=${route.params.id}&plot=full`
      )
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          movie.value = data;
        });
    });

    return {
      movie,
    };
  },
};
</script>
