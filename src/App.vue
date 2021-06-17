<template>
  <div id="app">
      
    <FilmList />
  </div>
</template>

<script>
import FilmList from "./components/FilmList.vue";




export default {
  name: 'App',
  components: {
    FilmList,
  }
    
}
</script>

<style lang="scss">
  // import
  @import "./style/general.scss";
</style>
