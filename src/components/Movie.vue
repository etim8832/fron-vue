<template>
    <div class="box">
        <h3 class="title"> {{movieId}} </h3>
        <div class="columns">
            <div  v-for="m in movies"  class="className(m.id)"  @click="chooseMovie(m.id)">  ถ้าไช้ loop จะขึ้น error แต่รันได้เฉยเลย 
                <figure class="image">
                    <img :src="imgSrc(m.id)">
               <!-- <img src="../../public/image/planet.jpg"> -->
                </figure>
      </div> 
     </div>
    </div> 
</template>

<script>
import { movies } from "../Others/movie.json";
console.log('show ',movies);
export default {
props:[ 'movieId'],
  data() {
    return {
      movies
      }
  },
  methods:{
      imgSrc(movieId){
          return `/movies/${movieId}.jpg`
      },
      chooseMovie(movieId){
    this.$emit('chooseMovie',movieId)
      },
      className(movieId){
          return [
              'comlumn', 'pointer',
              { 'chosen': this.movieId === movieId}
          ]
      }
    
  },  mounted(){
          this.chooseMovie(movies[0].id)
      }
}
</script>

<style>

.pointer{
    cursor:pointer;
}
chosen{
    border-style:solid;
}

</style>

