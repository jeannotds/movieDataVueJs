<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img src="../assets/story.jpg" class="feature-img" />
        <div class="detail">
          <h3>Naruto</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Adipisci
            dolorum obcaecati neque iure unde deleniti quos sit laborum culpa
            veniam repellendus labore consequatur placeat eligendi dignissimos
            aliquid accusantium, illum accusamus.
          </p>
        </div>
      </router-link>
    </div>
    <form @submit.prevent="SearchMovies()" class="search-box">
      <input
        class="input"
        type="text"
        placeholder="What are you looking for ?"
        v-model="search"
      />
      <input class="submit" type="submit" value="Search" />
    </form>
    <div class="movies-list">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'movie/' + movie.imdbID" class="movie-link">
          <div class="product-img">
            <img :src="movie.Poster" alt="" title="Movie Poster" />
            <div class="type">{{ movie.Type }}</div>
          </div>
          <div class="detail-movie">
            <p class="year"> {{ movie.Year }}</p>
            <h3>Title : {{ movie.Title }}</h3>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import env from "@/env.js";
export default {
  setup() {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        // console.log(search.value);
        fetch(
          `http://www.omdbapi.com/?i=tt3896198&apikey=${env.apiKeys}&s=${search.value}`
        )
          .then((res) => res.json())
          .then((data) => {
            // console.log(data);
            movies.value = data.Search;
            search.value = "";
            console.log(movies.value);
          });
      }
    };

    return {
      search,
      movies,
      SearchMovies,
    };
  },
};
</script>

<style>
.feature-card {
  position: relative;
}
.feature-img {
  display: block;
  width: 100%;
  height: 300px;
  opacity: 0.4;
  object-fit: cover;
  position: relative;
  z-index: 0;
}

.detail {
  position: absolute;
  /* top: 0; */
  right: 0;
  left: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.6);
  padding: 16px;
  z-index: 1;
}

h3 {
  color: rgba(255, 255, 255, 0.67);
  margin-bottom: 16px;
}

p {
  color: rgba(255, 255, 255, 0.67);
  margin-bottom: 16px;
}

.search-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

input {
  display: block;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}

.input {
  padding: 3px 5px;
  width: 100%;
  color: #fff;
  background-color: rgba(73, 101, 131, 0.4);
  font-size: 20px;
  padding: 10px 16px;
  border-radius: 3px;
  margin-bottom: 15px;
}

::placeholder {
  color: #f3f3f3;
  opacity: 0.67;
}

.input:focus {
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
}

.submit {
  max-width: 300px;
  background-color: rgba(0, 0, 0, 0.2);
  padding: 12px;
  border-radius: 8px;
  color: #fff;
  font-size: 20px;
  text-transform: uppercase;
  transition: 0.4s;
}
.submit:active {
  background-color: #3b8070;
}

.movies-list {
  display: flex;
  flex-wrap: wrap;
  margin: 0px 8px;
}

.movie {
  max-width: 50%;
  flex: 1 1 50%;
  padding: 16px 8px;
}

.movie-link {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.product-img {
  position: relative;
  display: block;
}

.product-img img {
  display: block;
  width: 100%;
  height: 275px;
  object-fit: cover;
}
.product-img .type {
  position: absolute;
  padding: 8px 16px;
  background-color: #42b884;
  color: #fff;
  bottom: 16px;
  left: 0;
  text-transform: capitalize;
}

.detail-movie {
  background-color: #496583;
  padding: 16px 8px;
  flex: 1 1 100%;
  border-radius: 0 0 8px 8px;
}

.year {
  background-color: #AAA;
  font-size: 14px;
  padding: 3px;
}

h3{
  color: white;
  font-weight: 600;
  font-size: 18px;
}
</style>
