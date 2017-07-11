<template>
  <div id="app">
    <Topbar/>
    <TopHeader/>
    <TopBanner/>
    <Slide/>
    <TopSub/>
    <GoodsStar/>
    <div id="main-page">
      <GoodsCollocation/>
      <GoodsIntelligence/>
    </div>
    
  </div>
</template>

<script>

import Topbar from './components/Topbar'
import TopHeader from './components/TopHeader'
import TopBanner from './components/TopBanner'
import Slide from './components/Slide'
import TopSub from './components/TopSub'
import GoodsStar from './components/GoodsStar'
import GoodsCollocation from './components/GoodsCollocation'
import GoodsIntelligence from './components/GoodsIntelligence'

export default {
  name: 'app',
  components: {Topbar,TopHeader,TopBanner,Slide,TopSub,GoodsStar,GoodsCollocation,GoodsIntelligence}
}
</script>

<style>
  html {
    width: 100%;
    height: 100%;
  }

  body {

    font: 14px/1.5 Helvetica, Arial, "Microsoft Yahei", "Hiragino Sans GB", "Heiti SC", "WenQuanYi Micro Hei", sans-serif;
    width: 100%;
    height: 100%;
  }
  
  * {
    margin: 0;
    padding: 0;
  }

  ul,li {
    list-style: none;
  }

  .clearfix:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden
  }
  .clearfix {
    *+height: 1%;
  }

  a {
    text-decoration: none;
    color: #333;
  }
  #main-page {
    width: 100%;
    padding-top: 60px;
    background: #f5f5f5;
  }
</style>
