<template>
<header>
  <router-link to="/">
   <h1><span>Vue </span>Movies</h1>
  </router-link>
</header>
 <main>
 <router-view />
 </main>
</template>


<script>
export default {
  
}
</script>


<style>
*{
margin: 0;
padding: 0;
box-sizing: border-box;  
font-family: 'Fira Sans', sans-serif;
}

body{
background-color: #35495E;  
color: #fff;
}

a{
text-decoration: none;
}

header{
margin: 0px auto;  
text-align: center;
background-color: #2C3D4E;
padding: 10px 16px;
box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);
}

h1{
color: #fff;
font-size: 28px;
}

h1 span{
color: #42B883;  
}

</style>
