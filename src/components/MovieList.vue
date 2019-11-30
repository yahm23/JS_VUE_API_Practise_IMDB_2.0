<template >
  <div >
    <single-movie v-for="(movie,index) in movies":movie="movie"> </single-movie>

  </div>
</template>

<script>
import SingleMovie from './SingleMovie.vue'
export default {
  name:'movie-list',
  components:{
    'single-movie': SingleMovie
  },
  props:['movies']
}
</script>

<style lang="css" scoped>
</style>
