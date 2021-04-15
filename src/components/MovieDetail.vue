<template>
 <div class="movie">
  <h2>Movie Title</h2>
 </div>   
</template>

<script>
import { ref, onBeforeMount } from 'vue';

export default {
name: 'MovieDetail', 
setup() {
const movie = ref({});
const route = useRoute()

return{
    
} 

}  
}
</script>

<style>

</style>
