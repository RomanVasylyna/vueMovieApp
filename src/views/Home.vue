<template>
  <div class="home">

    <div class="feature-card">
      <router-link to="/movie/tt0409591">
      <img src="https://images.ctfassets.net/hrltx12pl8hq/7yQR5uJhwEkRfjwMFJ7bUK/dc52a0913e8ff8b5c276177890eb0129/offset_comp_772626-opt.jpg?fit=fill&w=800&h=300" 
      alt="Dildo"
      class="feature-img">
      </router-link>
    </div>

    <div class="detail">
     <h3>Naruto</h3>
     <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit.
      Tempora magnam beatae obcaecati non perspiciatis quibusdam</p>
    </div>

    
    <!-- Search Bar -->
    <form @submit.prevent="" class="search-box">
     <input type="text" placeholder="What are you looking for?">
     <br>
     <input type="submit" value="Search">
    </form>

    <div class="movies-list">
      <MovieDetail/>
    </div>

  </div>
</template>

<script>
import { ref } from 'vue'; //Composition API

export default {
 
}
</script>

<style scoped>

.feature-card{
 position: relative; 
}

.feature-img{
 display: block;
 width: 100%;
 height: 300px;
 object-fit: cover;  /* То же самое что и background position но для картинок */

 position: relative;
 z-index: 0;  /* делаем картинку как бы задним фоном */
}

.detail {
 position: absolute; 
 left: 0;
 right: 0;
 bottom: 400px;
 padding: 15px;
 background: rgba(0, 0, 0, 0.5);
 z-index: 1;
}

.detail h3{
font-weight: bold;
margin-bottom: 16px;
}

.search-box{
display: flex;  
flex-direction: column;
justify-content: center;
align-items: center;
padding: 16px;
}

.search-box input[type="text"]{
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

input[type="text"]::placeholder{
color: #f3f3f3;  
}

input[type="text"]:focus{
box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
}

input[type="submit"]{
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
background: #42B883;  
}

input[type="submit"]:active{
background: #3B8070;  
}



</style>
