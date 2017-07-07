<template>
  <div id="topbar">
    <div class="topbar">
      <div class="topbar-nav">
        <ul class="nav-wrap">
          <li v-for="navItem in navItems" class="item">
            <a :href="navItem.url">{{navItem.name}}</a>
            <span class="separate">|</span>
          </li>
        </ul>
      </div>
      <div class="topbar-info">
        <ul class="info-wrap">
          <li v-for="infoItem in infoItems" class="item">
            <a :href="infoItem.url">{{infoItem.name}}</a>
            <span class="separate">|</span>
          </li>
        </ul>
      </div>
      <div class="topbar-cart" @mouseenter="isEnter" @mouseleave="isLeave">
        <div class="cart" :class="{'active': cartStatus}">
          <span class="iconfont">&#xe600;</span>
          <a href="https://static.mi.com/cart/">购物车</a>
          <span>( 0 )</span>
        </div>
        <transition name="fade">
          <div class="cart-list" v-show="cartStatus">购物车中还没有商品，赶紧选购吧！</div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    name: 'topbar',
    data() {
      return {
        navItems: [
          {name:'小米商城',url:'https://www.mi.com/index.html'},
          {name:'MIUI',url:'http://www.miui.com/'},
          {name:'米聊',url:'http://www.miliao.com/'},
          {name:'游戏',url:'http://game.xiaomi.com/hy/index.html'},
          {name:'多看阅读',url:'http://www.duokan.com/'},
          {name:'云服务',url:'https://i.mi.com/'},
          {name:'金融',url:'https://jr.mi.com/?from=micom'},
          {name:'小米商城移动版',url:'https://www.mi.com/appdownload/'},
          {name:'问题反馈',url:'https://static.mi.com/feedback/'},
          {name:'Select Region',url:'https://www.mi.com/#J_modal-globalSites'}
        ],
        infoItems: [
          {name:'登录',url:'https://order.mi.com/site/login?redirectUrl=https://www.mi.com/'},
          {name:'注册',url:'https://account.xiaomi.com/pass/register'},
          {name:'消息通知',url:'https://order.mi.com/message/list'}
        ],
        cartStatus: false
      }
    },
    methods: {
      isEnter: function(){
        this.cartStatus = true
      },
      isLeave: function(){
        this.cartStatus = false
      }
    }
  }
</script>

<style scoped lang="scss">
  @font-face {
    font-family: 'iconfont';  /* project id 345452 */
    src: url('//at.alicdn.com/t/font_bqfikrcdba4kuik9.eot');
    src: url('//at.alicdn.com/t/font_bqfikrcdba4kuik9.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_bqfikrcdba4kuik9.woff') format('woff'),
    url('//at.alicdn.com/t/font_bqfikrcdba4kuik9.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_bqfikrcdba4kuik9.svg#iconfont') format('svg');
  }
  #topbar {
    width: 100%;
    height: 40px;
    position: relative;
    font-size: 12px;
    color: #b0b0b0;
    background: #333;
    >.topbar {
      width: 1226px;
      margin-right: auto;
      margin-left: auto;
      line-height: 40px;
      height: 40px;  
      display: flex;
      justify-content: space-between;
      >.topbar-nav {
        overflow: hidden;
      }
      >.topbar-info {
        margin-left: auto;
      }
      >.topbar-cart {
        width: 120px;
        margin-left: 15px;
        position: relative;
        text-align: center;
        color: #b0b0b0;
        z-index: 20;
        background: #424242;
        &:hover {
          background: #fff;
          .cart {
            a,span {
            color: #ff6700;
            }
          }         
        }
        .active {
          background: #fff;
          a,span {
            color: #ff6700;
          }
        }
        .cart {
          position: relative;
          z-index: 20;
          .iconfont {
            font-family:"iconfont" !important;
            font-size: 14px;
            color: #b0b0b0;
          }
          a {
            color: #b0b0b0;
          }
        }
        .cart-list {
          position: absolute;
          z-index: 10;
          right: 0;
          top: 40px;
          font-size: 12px;
          text-align: center;
          width: 316px;
          line-height: 96px;
          height: 96px;
          color: #424242;
          background: #fff;
          box-shadow: 0 2px 10px rgba(0,0,0,0.15);
        }
      }
    }
  }
  ul {
    display: flex;
    >li:last-child .separate {
      display: none;
    }
    >li {
      >a {
        color: #b0b0b0;
        &:hover {
          color: #fff;
        }
      }
      >.separate {
        margin: 0 .5em;
        color: #424242;
      }
    }
  }
  .fade-enter-active, .fade-leave-active {
    transition: all .5s ease;
    height: 96px;
    opacity: 1;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
    height: 0;
  }
</style>