<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img
          src="https://m.media-amazon.com/images/M/MV5BZmQ5NGFiNWEtMmMyMC00MDdiLTg4YjktOGY5Yzc2MDUxMTE1XkEyXkFqcGdeQXVyNTA4NzY1MzY@._V1_SX300.jpg"
          alt="Dildo"
          class="feature-img"
        />
      </router-link>
    </div>

    <div class="detail">
      <h3>Naruto</h3>
      <p>
       Naruto Uzumaki, a mischievous adolescent ninja, struggles as he searches
       for recognition and dreams of becoming the Hokage, the village's leader
       and strongest ninja.
      </p>
    </div>

    <!-- Search Bar -->
    <form @submit.prevent="SearchMovies" class="search-box">
      <input
        type="text"
        placeholder="What are you looking for?"
        v-model="search"
      />
      <input type="submit" value="Search" />
    </form>

    <div class="movies-list" v-for="movie in movies" :key="movie.imdbID">
      <div class="movie">

      <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
      <div class="product-img">
       <img class="movie-img" :src="movie.Poster" alt="Movie Poster">
      </div>
      </router-link>

      <div class="movie-type">{{ movie.Type }}</div>
      <div class="movie-detail">
        <p class="movie-year">{{ movie.Year }}</p>
        <h3 class="movie-title">{{ movie.Title }}</h3>
      </div>

      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue"; //Composition API
import env from "@/env.js"

export default {
  setup() {
    const search = ref(""); // Search query from input
    const movies = ref([]); //Array of movies to display in the bottom

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(
          `http://www.omdbapi.com?s=${search.value}&apikey=${env.apiKey}`
        )
          .then(res => res.json())
          .then(data => {
          movies.value = data.Search;
          search.value = "";
          console.log(data);
          console.log(movies);
          })
          .catch(err => console.log(err));
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

<style scoped>
.feature-card {
  position: relative;
}

.feature-img {
  display: block;
  width: 100%;
  height: 300px;
  object-fit: cover; /* То же самое что и background position но для картинок */

  position: relative;
  z-index: 0; /* делаем картинку как бы задним фоном */
}

.detail {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 52vh;
  padding: 15px;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

.detail h3 {
  font-weight: bold;
  margin-bottom: 16px;
}

.search-box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

.search-box input[type="text"] {
  width: 100%;
  display: block;
  border: none;
  outline: none;
  background-color: #496583;
  color: #fff;
  font-size: 20px;
  padding: 10px 16px;
  border-radius: 8px;
  margin-bottom: 15px;
  transition: 0.4s;
}

input[type="text"]::placeholder {
  color: #f3f3f3;
}

input[type="text"]:focus {
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
}

input[type="submit"] {
  width: 100%;
  max-width: 300px;
  border: none;
  outline: none;
  color: #fff;
  font-size: 20px;
  padding: 16px;
  border-radius: 8px;
  text-transform: uppercase;
  transition: 0.4s;
  background: #42b883;
}

input[type="submit"]:active {
  background: #3b8070;
}

.movies-list{
display: flex;
flex-wrap: wrap;
margin: 0px 8px;
}

.movie{
max-width: 50%;
flex: 1 1 50%;
padding: 16px 8px;
}

.movie-link{
display: flex;
flex-direction: column;
}

.product-img{
display: block;
position: relative;
}

.movie-img{
display: block;
width: 100%;
height: 275px;
object-fit: cover;
}

.movie-type{
position: absolute;
background-color: #42B883;
padding: 8px 16px;
bottom: 16px;
text-transform: capitalize;
}

.movie-detail{
background-color: #496583;
padding: 16px 8px;
border-radius: 0px 0px 10px 10px;
flex: 1 1 100%;
}

.movie-year{
color: #AAA;
font-size: 14px;
}
</style>
