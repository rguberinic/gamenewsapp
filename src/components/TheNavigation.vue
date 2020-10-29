<template>
  <div id="nav">
    <h1>Super Original Console Segga 999999999 in 1</h1>
    <input type="text" placeholder="Begin the search" v-model='searchGame'>
    <button v-if="!showNewsWindow" @click='handleSearchNews'>Trigger</button>
    <button v-if="showNewsWindow" @click='handleShowNewsWindow'>Go back</button>
  </div>
</template>

<script>
export default {
  props:['showNewsWindow'],
  data () {
    return {
      searchGame:''
    }
  },
  methods: {
    handleSearchNews () {
      this.$emit('handleSearchNews',this.searchGame)
    },
    handleShowNewsWindow () {
      this.$emit('handleShowNewsWindow', false)
    }
  }
}
</script>

<style lang='scss'>
  #nav {
    width: 100%;
    min-height: 8%;
    background-color: #3e6a91;
    display: flex;
    align-items: center;
    justify-content: space-between;

    h1 {
      margin: 0 0 0 1%;
      color:#fff;
      font-family: 'Turret Road', cursive;
    }

    input  {
      background: white;
      margin: 0 1% 0 0;
      padding: 0 0.09%;
      width: 300px;
      height: 30%;
    }
    button {
      display: none;
    }
  }
  @media screen and (max-width: 920px) {
    #nav {
      text-align: center;
      flex-direction: column;
    }
    h1 {
      font-size: 1.5em;
    }
    input {
      margin:0 0 5px 0 !important;
    }
    button {
      display: block !important;
      width: 40%;
    }
  }

  @media screen and (max-width: 280px) {
    #nav {
      input {
        width: 250px;
      }
    }
  }
</style>