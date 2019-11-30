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
  methods:{
  handleClick(){
  eventBus.$emit("movie-selected", this.movie)
    }
  }
}
</script>

<style lang="css" scoped>
container1
</style>
