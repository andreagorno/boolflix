<template>
  <div id="app">
      <!-- <Header/> -->
      <FilmList />
  </div>
</template>

<script>
import FilmList from "./components/FilmList.vue"
// import Header from "./components/Header.vue"


export default {
  name: 'App',
  components: {
    FilmList,
    // Header
  }
}
</script>

<style lang="scss">
  // import
  @import "./style/general.scss";
</style>
