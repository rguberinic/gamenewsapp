<template>
  <f7-app id="app">
    <TheNavigation @handleSearchNews='searchNews' :showNewsWindow='showNewsWindow' @handleShowNewsWindow='handleShowNewsWindow'/>
    <Main v-if='!showNewsWindow' :gamesArr='gamesArr' @toggleNewsView='toggleNewsView' @handleGetNews='handleGetNews'/>
    <NewsDisplay :currentSelectedNewsArr='currentSelectedNewsArr'/>
 
  </f7-app>
</template>
<script>
  import axios from 'axios'
  import TheNavigation from '../components/TheNavigation'
  import Main from '../components/Main'
  import NewsDisplay from '../components/NewsDisplay'
  import routes from '../js/routes.js';

  export default {
    components: {
      TheNavigation,
      Main,
      NewsDisplay
    },

    data() {
      return {
        gamesArr:[],
        showNewsWindow:false,
        currentSelectedNewsArr:null
      }
    },
    methods: {
      searchNews(searchGame) {
        axios.get('http://097a122.e2.mars-hosting.com/games/search-games', {
          params: {
            searchGame:searchGame
          }
        })
        .then((response) =>  {
          this.gamesArr = []
          this.gamesArr = response.data.games
        })
        .catch((e) => {
          console.log(e);
        })
      },
      toggleNewsView (bool) {
        this.showNewsWindow = bool
      },
      handleGetNews (gameId) {
        axios.get('http://097a122.e2.mars-hosting.com/games/steam-news',{
          params:{
            steamId:gameId
          }
        })
        .then((response) => {
          if(response.data.news){
            this.showNewsWindow = true
            this.currentSelectedNewsArr = response.data.news.newsitems
            console.log(this.currentSelectedNewsArr)
          }
          else{
            console.log('there are not any news')
          }
        })
        .catch((error) => {
          console.log(error);
        })
      },
      handleShowNewsWindow (bool) {
        this.showNewsWindow = bool
      }
    },
    mounted() {
      this.$f7ready((f7) => {

      });
    }
  }
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Turret+Road:wght@400;500;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');
  #app {
    min-height: 100%;
    background-color: #000;
    overflow: scroll;
  }
</style>