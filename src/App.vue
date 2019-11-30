<template lang="html">
  <div class="">
      <h1>IMDB Rip Off</h1>
      <form v-on:submit.prevent="handleSearch">
        <h2>Search for a Movie</h2>
        <input type="text" v-model="search" value="Type here">
        <input type="submit" value="Search">
      </form>

      <movie-list :movies="movies"></movie-list>
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
      allResults:''
    }
  },
  mounted(){
    eventBus.$on("movie-selected", movie=> {this.selectedMovie = movie})
  },
  methods:{
    handleSearch(){
      fetch(`http://www.omdbapi.com/?s=${this.search}&page=1&apikey=1a23941a`)
      .then(result => result.json())
      .then(data => this.movies = data['Search'])
    },
    computed(){
      // searchResults: this.allResults['Search']
    }

  }
}
</script>

<style lang="css" scoped>
</style>
