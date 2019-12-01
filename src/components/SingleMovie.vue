<template >
  <div class="container1">
    <h2 v-on:click="handleClick" :value="movie">{{movie.Title}}</h2>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name:'single-movie',
  props:['movie'],
  data(){
    return{
      value:''
    }
  },
  methods:{
    handleClick(){
    eventBus.$emit("movie-selected", this.movie)

    fetch(`http://www.omdbapi.com/?i=${this.movie.imdbID}&page=1&apikey=1a23941a`)
    .then(result => result.json())
    .then(data =>this.value = data)

    eventBus.$emit("movie-selectedResults", this.value)

      }
    }


}
</script>

<style lang="css" scoped>
  .container1{
  font-family: cursive;
  border-radius: 3px solid slategrey;
  }
</style>
