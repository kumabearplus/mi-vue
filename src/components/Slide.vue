<template>
<div id="main-carousel">
  <div class="main-carousel">
    <div class="container">
      <transition-group name="fade" tag="div" class="fade">
        <div class="fade-item" v-for="(item,index) in fadeItems" v-show="index === curIndex" :key="index">
          <a :href="item.link">
            <img :src="item.imgUrl" alt="">
          </a>
        </div>
      </transition-group>
      <div class="play-pre" @click="playPre">
        <span class="icon"></span>
      </div>
      <div class="play-next" @click="playNext">
        <span class="icon"></span>
      </div>
      <div class="play-dot">
        <span class="dot" v-for="n in 6" :class="{active: n === curIndex + 1}" :key="n" @click="play(n-1)">{{n}}</span>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  data(){
    return{
      curIndex: 0,
      timeId: '',
      fadeItems: [
        {imgUrl: './static/imgs/xmad1.jpg', link: 'https://hd.mi.com/x/07051r/index.html?client_id=180100041086&ma%E2%80%8Bsid=17409.0068'},
        {imgUrl: './static/imgs/xmad2.jpg', link: 'https://item.mi.com/product/10000057.html'},
        {imgUrl: './static/imgs/xmad3.jpg', link: 'https://item.mi.com/buyphone/redmi4x'},
        {imgUrl: './static/imgs/xmad4.jpg', link: 'https://www.mi.com/hot/'},
        {imgUrl: './static/imgs/xmad5.jpg', link: 'https://www.mi.com/mibookair/'},
        {imgUrl: './static/imgs/xmad6.jpg', link: 'https://hd.mi.com/x/06282u/index.html?client_id=180100041086&masid=17409.0069'}
      ]
    }
  },
  mounted(){ //Vue2.0 替换了之前的ready，详见文档生命周期函数mounted
    this.autoPlay()
  },
  methods: {
    playNext(){
      let lastIndex = this.fadeItems.length -1
      if(this.curIndex < lastIndex){
        this.curIndex += 1
      }else{
        this.curIndex = 0
      }
    },
    playPre(){
      let lastIndex = this.fadeItems.length - 1
      if(this.curIndex > 0){
        this.curIndex -= 1
      }else{
        this.curIndex = lastIndex
      }
    },
    play(n){
      this.curIndex = n
    },
    autoPlay(){
      clearInterval(this.timeId)
      this.timeId = setInterval(()=>{
        this.playNext()
      }, 4000)
    }
  }
}
</script>

<style scoped lang="scss">
  #main-carousel {
    position: relative;
    width: 1226px;
    height: 460px;
    z-index: 0;
    margin: 0 auto;
    >.main-carousel{
      position: absolute;
      left: 0;
      top: 0;
      width: 1226px;
      height: 460px;
      z-index: 1;
      .container{
        position: relative;
        height: 460px;
        .fade-item{
          position: absolute;
          left: 0;
          top: 0;
          z-index: 1;
          img {
            width: 1226px;
            height: 460px;
          }
        }
        .play-pre{
          position: absolute;
          left: 234px;
          top: 50%;
          margin-top: -35px;
          z-index: 2;
          .icon{
            width: 41px;
            height: 69px;
            background: url(../assets/icon-slides.png) no-repeat;
            background-position: -83px 50%;
            display: inline-block;
            cursor: pointer;
            &:hover{
              background: url(../assets/icon-slides.png) no-repeat;
              background-position: 1px 50%;
            }
          }
        }
        .play-next{
          position: absolute;
          right: 0;
          top: 50%;
          margin-top: -35px;
          z-index: 2;
          .icon{
            width: 41px;
            height: 69px;
            background: url(../assets/icon-slides.png) no-repeat;
            background-position: -124px 50%;
            display: inline-block;
            cursor: pointer;
            &:hover{
              background: url(../assets/icon-slides.png) no-repeat;
              background-position: -42px 50%;
            }
          }
        }
        .play-dot{
          position: absolute;
          z-index: 1;
          width: 100px;
          right: 20px;
          bottom: 20px;
          display: flex;
          justify-content: space-between;
          .dot{
            cursor: pointer;
            width: 6px;
            height: 6px;
            font-size: 0;
            border: 2px solid rgba(255,255,255,0.5);
            border-radius: 50%;
            background: rgba(0,0,0,0.5);
          }
          .active{
            border-color: rgba(0,0,0,0.5);
            background: rgba(255,255,255,0.5);
          }
        }
      }
    }
  }
  
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>