<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div style="display: flex; justify-content: center">
      <Marquee :tipList="tipList" :showAvatar="false" :width="500" ></Marquee>
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
        '张三获得了一台笔记本电脑',
        '二狗子获得了一台笔记本电脑',
        'Tracy获得了一箱冰淇淋'
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
