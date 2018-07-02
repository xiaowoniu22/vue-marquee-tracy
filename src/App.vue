<template>
  <div id="app">
    <div style="display: flex; align-items: center; flex-direction: column">
      <span>获奖名单</span>
      <Marquee :tipList="tipList" :width="500" ></Marquee>
    </div>
  </div>
</template>

<script>
import Marquee from './components/Marquee'
export default {
  name: 'App',
  components: {
    Marquee
  },
  data: function () {
    return {
      tipList: [
        'A获得了一台笔记本电脑',
        'B获得了一台液晶电视',
        'c获得了一台ipad'
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
