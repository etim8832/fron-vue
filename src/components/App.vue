<template>
<div class="box">
    <h2 class="title"> App : {{ movieId}} </h2>
    <movie  @chooseMovie="handleChooseMovie" :movieId="movieId"/>
    <Seat 
    :movieId="movieId"
     @chooseSeat="handleChooseSeat"
     :selectSeats="selectSeats"
     />
</div>
</template>

<script>
import Movie from 'Components/Movie.vue'
import Seat from 'Components/Seat.vue'
export default {
    components : { Movie , Seat },
    data(){
        return{
            movieId:'',
            selectSeats:[]
        }
    },
    methods:{
        handleChooseMovie(movieId){
            console.log('ok');
            this.movieId = movieId;
        },
        handleChooseSeat(seat){
      const ids = this.selectSeats.map(s => s.id);
      const idx = ids.indexOf(seat.id)
      if(idx === -1){
          this.selectSeats.push(seat)
      } else{
          this.selectSeats.splice(idx,1);
      }
        
        }
    }
}
</script>