<template >
  <div class="">
    <div v-if='selectedMovieResults'>
      <h2>{{selectedMovieResults.Title}}</h2>
      <h3></h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'movie-detail',
  props:['selectedMovieResults'],
  data(){
    return{


    }
  },
  // mounted:{
  //     fetch(`http://www.omdbapi.com/?i=${selectedMovie.imdbID}&page=1&apikey=1a23941a`)
  //     .then(result => result.json())
  //     .then(data => this.selectedMovie2 = data)
  //   }
}
</script>

<style lang="css" scoped>
</style>
