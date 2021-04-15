<template>
 <div class="movie">
  <h2>{{ movie.Title }}</h2>
  <p>{{ movie.Year }}</p>
  <img :src=movie.Poster alt="Movie Poster" class="featured-img">
  <p>{{ movie.Plot }}</p>
 </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from '@/env.js';

export default {
name: 'MovieDetail',

setup() {
const movie = ref({});
const route = useRoute();

onBeforeMount(() => {
        fetch(
          `http://www.omdbapi.com?i=${route.params.id}&apikey=${env.apiKey}&plot=full`
        )
          .then(res => res.json())
          .then(data => {
          movie.value = data;
          console.log(data);
          })
          .catch(err => console.log(err));
})

return{
movie,
route,
env
}

}
}
</script>

<style>
.movie{
font-size: 16px;
margin: 15px;
}
h2{
color: #fff;
font-size: 28px;
font-weight: 600;
margin-bottom: 16px;
}

.featured-img{
display: block;
max-width: 200px;
margin-bottom: 16px;
}

p{
color: #fff;
font-size: 18px;
line-height: 1.4;
}
</style>
