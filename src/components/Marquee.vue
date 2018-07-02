<template>
  <div class="marquee" :style="{width: width+'px'}">
    <ul class="marquee_ul" :style="{width: marqueeWidth+'px'}">
      <li :key="index" v-for="(tip,index) in tipList" class="marquee-li">
        <img v-if="showAvatar" :src="avatar" width="43" height="40"/>
        <span :style="{ paddingRight: distance + 'px'}">{{tip}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'marquee',
  data: function () {
    return {
      marqueeWidth: ''
    }
  },
  props: {
    tipList: {
      type: Array,
      default: function () {
        return []
      }
    },
    avatar: {
      type: String,
      default: require('../../static/head.png')
    },
    width: {
      type: Number,
      default: 700
    },
    distance: {
      type: Number,
      default: 100
    },
    showAvatar: {
      type: Boolean,
      default: true
    }
  },
  mounted () {
    const tips = document.getElementsByClassName('marquee-li')
    let totalWidth = 0
    for (let i = 0; i < tips.length; i++) {
      if (this.showAvatar) {
        totalWidth += tips[i].children[0].width + tips[i].children[1].offsetWidth
        tips[i].style.width = tips[i].children[0].width + tips[i].children[1].offsetWidth + 'px'
      } else {
        totalWidth += tips[i].children[0].offsetWidth
        tips[i].style.width = tips[i].children[0].offsetWidth + 'px'
      }
    }
    this.marqueeWidth = totalWidth
    const rule = `@keyframes mymove{
                0%   {left:${this.width}px;}
                100% {left:-${this.marqueeWidth}px;}
              }`
    if (document.styleSheets && document.styleSheets.length) {
      document.styleSheets[0].insertRule(rule, 0)
    }
  }
}
</script>

<style scoped>
  .marquee{
    line-height: 40px;
    margin: 10px 0 80px;
    overflow: hidden;
    transition: all 0.5s;
  }
  .marquee_ul{
    height: 50px;
    position: relative;
    animation:mymove 20s linear infinite;
    -moz-animation:mymove 20s linear infinite; /* Firefox */
    -webkit-animation:mymove 20s linear infinite; /* Safari and Chrome */
    -o-animation:mymove 20s linear infinite; /* Opera*/
  }
  .marquee_ul li{
    height: 50px;
    text-align: center;
    float: left;
    list-style: none;
    display: flex;
  }
  .marquee_ul li span{
    display: inline-block;
    white-space: nowrap;
  }
</style>
