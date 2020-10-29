<template>
  <div id="news-display">
    <div v-for="(news,idx) in currentSelectedNewsArr" :key='idx'>
      <h2>{{news.title}}</h2>
      <span v-html="news.contents"></span>
    </div>
  </div>
</template>

<script>
export default {
  props:[
    'currentSelectedNewsArr'
  ]
}
</script>

<style lang='scss'>
  #news-display {
    background-color: aliceblue;
    height: 92%;
    overflow: scroll;

    h2 {
      text-align: center;
    }
    img {
      display: block;
      margin: 0 auto;
    }
    p {
      text-align: center;
    }
  }
</style>