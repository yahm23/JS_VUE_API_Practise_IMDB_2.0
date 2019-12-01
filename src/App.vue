<template lang="html">
  <div class="">
    <div>
      <h1>IMDB Rip Off</h1>
        <form v-on:submit.prevent="handleSearch">
          <h2>Search for a Movie</h2>
          <input type="text" v-model="search" value="Type here">
          <input type="submit" value="Search">
        </form>
        <movie-list :movies="movies"></movie-list>
      </div>
      <movie-detail :selectedMovieResults="selectedMovieResults"></movie-detail>

    </div>
</template>

<script>

import {eventBus} from './main.js'
import MovieList from './components/MovieList.vue'
import MovieDetails from './components/MovieDetails.vue'

export default {
  name:'app',
  components:{
    'movie-list':MovieList,
    'movie-detail':MovieDetails
  },

  data(){
    return{
      selectedMovie:'',
      movies:'',
      search:'',
      allResults:'',
      selectedMovieResults:''
    }
  },

  mounted(){
    eventBus.$on("movie-selected", movie=> {this.selectedMovie = movie})
    eventBus.$on("movie-selectedResults", movie=> {this.selectedMovieResults = movie})
  },

  methods:{
    handleSearch(){
      fetch(`http://www.omdbapi.com/?s=${this.search}&page=1&apikey=1a23941a`)
      .then(result => result.json())
      .then(data => this.movies = data['Search'])

    }
  },

  computed:{
    // selectedMovie2(){ if (this.selectedMovie){
    //   fetch(`http://www.omdbapi.com/?i=${this.selectedMovie.imdbID}&page=1&apikey=1a23941a`)
    //   .then(result => result.json())
    //   .then(data => this.selectedMovieResults = data)}}
    },
  }


</script>

<style lang="css" scoped>
</style>
