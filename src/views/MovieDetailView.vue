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

<style>
    .movie-detail{
        padding: 16px;
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    .movie-detail h2{
        font-size: 28px;
        font-weight: 600;
        color: #FFF;
        margin-bottom: 16px;
    }

    .movie-detail .featured-img{
        display: block;
        max-width: 200px;
        margin-bottom: 16px;
        width: 100%;
    }

    p{
        color: #FFF;
        font-size: 18px;
        line-height: 1.4;
    }

</style>