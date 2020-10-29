<template>
  <div id="main">
    <div v-for="(game,idx) in gamesArr" :key='game.stg_id' class="game-preview">
      <span>
        {{idx+1}}.
        {{game.stg_name}}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props:[
    'gamesArr'
  ]
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
      height: 100%;
      color: #fff;
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