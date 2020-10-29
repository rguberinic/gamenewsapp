<template>
  <div id="main">
    <div v-for="(game,idx) in gamesArr" :key='game.stg_id' class="game-preview" @click='handleGetNews(game.stg_id)'>
      <span>
        {{idx+1}}.
        {{game.stg_name}}
      </span>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      
    }
  },
  props:[
    'gamesArr'
  ],
  methods: {
    handleGetNews (gameId) {
      this.$emit('handleGetNews', gameId)
    }
  }
}
</script>

<style lang='scss'>
  #main {
    min-height: 100%;
    width: 100%;
    background-color: #913e54;
    overflow-y: scroll;
    font-family: 'Roboto', sans-serif;
    font-weight: 500;

    .game-preview {
      width: 100%;
      height: 92%;
      color: #fff;
      cursor: pointer;
      span {
        font-size: 1.2em;
        display: block;
        margin: 5px 0;
      }
    }
  }
  @media screen and (max-width: 500px) {
    #main {
      text-align: center;
    }
  }
</style>