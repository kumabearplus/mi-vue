<template>
  <div id="top-header">
    <div class="container">
      <a href="https://www.mi.com/index.html" class="logo"></a>
      <a href="https://1.hd.mi.com/" class="pic-gif"></a>
      <div class="header-nav">
        <ul class="nav-wrap">
          <li v-for="navItem in navItems" class="item" @mouseleave="isLeave()">
            <a href="javascript: void(0);" @mouseenter="isEnter(navItem.type)"
              >{{navItem.name}}</a>
          </li>
        </ul>
      </div>
      <div class="header-search">
        <transition name="fadeOut">
          <div class="hot-word" v-show="hotStatus">
            <ul class="hot-wrap">
              <li v-for="hotItem in hotItems" class="item">{{hotItem}}</li>
            </ul>
          </div>  
        </transition> 
        <input type="" name="search" class="search-ipt" @focus="isFocus"
          @blur="isBlur">
        <label class="search-btn" for="search">
          <span class="iconfont">&#xe61d;</span>
        </label>
        <div class="search-result">
          <ul class="result-wrap">
            <li v-for="resultItem in resultItems" class="item">
              <span class="item-name">{{resultItem.Key}}</span>
              <span class="item-num">约有{{resultItem.Rst}}件</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <transition name="fadeIn">
      <div class="header-menu"
      @mouseenter="isEnter()"
      @mouseleave="isLeave()"
      v-show="headerStatus">
        <ul class="menus">
          <li class="product" v-for="tabItem in tabItems">
            <p class="info" v-show="tabItem.showStatus"><span class="flag">{{tabItem.info}}</span></p>
            <a :href="tabItem.link"><img :src="tabItem.imgUrl" :alt="tabItem.name"></a>
            <p class="name">{{tabItem.name}}</p>
            <p class="price">{{tabItem.price}}</p>
          </li>
        </ul>
      </div>
    </transition>   
  </div>
</template>

<script type="text/javascript">

import $ from 'jquery'

  export default {
    name: 'topHeader',
    data(){
      return {
        hotStatus: true,
        headerStatus: false,
        tids: '',
        navItems: [
          {name: '小米手机', type: 'xiaomi'},
          {name: '红米', type: 'redmi'},
          {name: '平板·笔记本', type: 'mipad'},
          {name: '电视', type: 'mitv'},
          {name: '盒子·影音', type: 'mibox'},
          {name: '路由器', type: 'mirouter'},
          {name: '智能硬件', type: 'mihardware'},
          {name: '服务',type: ''},
          {name: '社区',type: ''}
        ],
        hotItems: ['小米电视4A 直降300','小米5c'],
        resultItems: [
          {'Key':'小米6','Rst':7},
          {'Key':'红米Note 4X','Rst':8},
          {'Key':'小米MIX','Rst':1},
          {'Key':'小米Max2','Rst':3},
          {'Key':'小米手机5c','Rst':3},
          {'Key':'手环','Rst':6},
          {'Key':'耳机','Rst':19},
          {'Key':'充电宝','Rst':19},
          {'Key':'运动鞋','Rst':2},
          {'Key':'路由器','Rst':17},
          {'Key':'小米盒子','Rst':8}
        ],
        tabItems: ["xiaomi","redmi","mipad","mitv","mibox","mirouter","mihardware"],
        "xiaomi": [
          {name: '小米6', imgUrl: './static/imgs/xm6.png', link: 'https://www.mi.com/mi6/', price: '2499元起', info: '新品' ,showStatus: true},
          {name: '小米Max 2', imgUrl: './static/imgs/max2.png', link: 'https://www.mi.com/max2/', price: '1699元起', info: '现货' ,showStatus: true},
          {name: '小米Note 2', imgUrl: './static/imgs/xiaomiNOTE2.jpg', link: 'https://www.mi.com/minote2/', price: '2799元起', info: '立减300' ,showStatus: true},
          {name: '小米MIX', imgUrl: './static/imgs/MIX.jpg', link: 'https://www.mi.com/mix/', price: '3499元起', info: '特惠250' ,showStatus: true},
          {name: '小米5s Plus', imgUrl: './static/imgs/5splus.jpg', link: 'https://www.mi.com/mi5splus/', price: '2299元起', info: '立减200' ,showStatus: true},
          {name: '小米手机5c', imgUrl: './static/imgs/mi5c.png', link: 'https://www.mi.com/mi5c/', price: '1499元起', info: '立减200' ,showStatus: true},
        ],
        "redmi": [
          {name: '红米Note 4X', imgUrl: './static/imgs/hmn4x.jpg', link: 'https://www.mi.com/redminote4x/', price: '799元起', info: '热卖' ,showStatus: true},
          {name: '红米4X', imgUrl: './static/imgs/hm4x.jpg', link: 'https://www.mi.com/redmi4x/', price: '699元起', info: '热卖' ,showStatus: true},
          {name: '红米4A', imgUrl: './static/imgs/hm4a.png', link: 'https://www.mi.com/redmi4a/', price: '599元起', info: ''},
          {name: '红米4', imgUrl: './static/imgs/hm4.jpg', link: 'https://www.mi.com/redmi4', price: '799元起', info: ''},
        ],
        "mipad": [
          {name: '小米平板3 64GB', imgUrl: './static/imgs/mipad3.png', link: 'https://www.mi.com/mipad3/', price: '1499元', info: ''},
          {name: '小米笔记本Air 12.5', imgUrl: './static/imgs/bijiben12.5.jpg', link: 'https://www.mi.com/mibookair-12/', price: '3599元', info: ''},
          {name: '小米笔记本Air 13.3', imgUrl: './static/imgs/bijiben13.3.jpg', link: 'https://www.mi.com/mibookair/', price: '4999元', info: '新品' ,showStatus: true}
        ],
        "mitv": [
          {name: '小米电视4 49英寸', imgUrl: './static/imgs/xmds_49.png', link: 'https://www.mi.com/mitv4/49/', price: '3499元', info: '新品' ,showStatus: true},
          {name: '小米电视4 55英寸', imgUrl: './static/imgs/xmds_55.png', link: 'https://www.mi.com/mitv4/55/', price: '3999元起', info: '新品' ,showStatus: true},
          {name: '小米电视4 65英寸', imgUrl: './static/imgs/xmds_65.png', link: 'https://www.mi.com/mitv4/65/', price: '9999元', info: '新品' ,showStatus: true},
          {name: '小米电视4A 43英寸', imgUrl: './static/imgs/xmds4a_43.png', link: 'https://www.mi.com/mitv4A/43/', price: '2099元', info: ''},
          {name: '小米电视4A 49英寸', imgUrl: './static/imgs/xmds4a_49.png', link: 'https://www.mi.com/mitv4A/49/', price: '2599元', info: ''},
          {name: '查看全部', imgUrl: './static/imgs/70dianshi.png', link: 'https://www.mi.com/mitv4A/49/', price: '小米电视', info: ''}
        ],
        "mibox": [
          {name: '小米盒子3s', imgUrl: './static/imgs/mihezi3s.png', link: 'https://www.mi.com/mibox3s/', price: '299元', info: ''},
          {name: '小米盒子3c', imgUrl: './static/imgs/mihezi3c.png', link: 'https://www.mi.com/mibox3c/', price: '199元', info: ''},
          {name: '小米盒子3 增强版', imgUrl: './static/imgs/hezi3s.jpg', link: 'https://www.mi.com/hezi3s/', price: '399元', info: ''},
          {name: '小米家庭影院', imgUrl: './static/imgs/jtyy.png', link: 'https://www.mi.com/misurround/', price: '1999元', info: ''},
          {name: '小米家庭音响 标准版', imgUrl: './static/imgs/putonban.jpg', link: 'https://item.mi.com/1160800074.html', price: '699元', info: ''}
        ],
        "mirouter": [
          {name: '小米路由器 HD/Pro', imgUrl: './static/imgs/HD-Pro.png', link: 'https://www.mi.com/miwifihd/', price: '499元起', info: ''},
          {name: '小米路由器 3G', imgUrl: './static/imgs/3G.png', link: 'https://www.mi.com/miwifi3g/', price: '249元', info: '新品' ,showStatus: true},
          {name: '小米路由器 3', imgUrl: './static/imgs/xmlyq3.png', link: 'https://www.mi.com/miwifi3/', price: '149元起', info: '包邮' ,showStatus: true},
          {name: '小米路由器 3C', imgUrl: './static/imgs/3C.png', link: 'https://www.mi.com/miwifi3c/', price: '99元', info: '包邮' ,showStatus: true},
          {name: '小米WiFi电力猫', imgUrl: './static/imgs/dlm.png', link: 'https://www.mi.com/plc/', price: '249元', info: ''},
          {name: '小米WiFi放大器 2', imgUrl: './static/imgs/fdq2.jpg', link: 'https://item.mi.com/1164700010.html', price: '49元', info: ''}
        ],
        "mihardware": [
          {name: '小米体脂秤', imgUrl: './static/imgs/tzc.jpg', link: 'https://www.mi.com/scale2/', price: '199元', info: ''},
          {name: '小米手环2', imgUrl: './static/imgs/sh2.png', link: 'https://www.mi.com/shouhuan2/', price: '149元', info: '包邮' ,showStatus: true},
          {name: '小米净水器', imgUrl: './static/imgs/jsqcs.png', link: 'https://www.mi.com/water3/', price: '1499元起', info: '新品' ,showStatus: true},
          {name: '小米VR眼镜 PLAY2', imgUrl: './static/imgs/xmvrplay2.png', link: 'https://www.mi.com/mivr2c/', price: '99元', info: '新品' ,showStatus: true},
          {name: '米家IH电饭煲', imgUrl: './static/imgs/dfb.jpg', link: 'https://www.mi.com/dianfanbao2/', price: '399元', info: ''},
          {name: '查看全部', imgUrl: './static/imgs/air2.jpg', link: 'https://www.mi.com/smart/', price: '智能硬件', info: ''}
        ]
      }
    },
    methods: {
      isFocus () {
        $('.header-search').addClass('search-active')
        $('.search-result').show()
        this.hotStatus = false
      },
      isBlur () {
        $('.header-search').removeClass('search-active')
        $('.search-result').hide()
        this.hotStatus = true
      },
      isEnter (menuType) {
        if (menuType) {
          this.tabItems = this[menuType]
          this.headerStatus = true
        } else if (menuType ==='') {
          this.headerStatus = false
        }
        clearTimeout(this.tids)
      },
      isLeave () {
        let self = this
        this.tids = setTimeout(function () {
          self.headerStatus = false
        }, 300)
      }
    }
  }
</script>

<style type="text/css" scoped lang="scss">
  @font-face {
    font-family: 'iconfont';  /* project id 347808 */
    src: url('//at.alicdn.com/t/font_xqxs22iapl9885mi.eot');
    src: url('//at.alicdn.com/t/font_xqxs22iapl9885mi.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_xqxs22iapl9885mi.woff') format('woff'),
    url('//at.alicdn.com/t/font_xqxs22iapl9885mi.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_xqxs22iapl9885mi.svg#iconfont') format('svg');
  }
  #top-header {
    width: 100%;
    height: 100px;
    >.container {
      position: relative;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      width: 1226px;
      height: 100%;
      margin: 0 auto;
      >.logo {
        width: 55px;
        height: 55px;
        background: url(../assets/mi-logo.png) no-repeat 50% 50% #ff6700;
      }
      >.pic-gif {
        width: 163px;
        height: 66px;
        margin-left: 10px;
        background: url(../assets/boom.gif) no-repeat 50% 50%;
      }
      >.header-nav {
        position: relative;
        >.nav-wrap {
          display: flex;
          height: 88px;
          line-height: 88px;
          >.item {
            font-size: 16px;
            padding: 0 10px;
            &:hover a {
              color: #ff6700;
            }
          }
        }
      }
      >.header-search {
        position: absolute;
        top: 23px;
        right: 0;
        width: 295px;
        height: 50px;
        display: flex;
        justify-content: space-between;
        border: 1px solid #e0e0e0;
        &.search-active {
          border: 1px solid #ff6700;
          .search-btn {
            border-left: 1px solid #ff6700;
          }
        }
        .hot-word {
          position: absolute;
          top: 14px;
          right: 62px;
          z-index: 2;
          text-align: right;
          >.hot-wrap {
            display: flex;
            >li {
              height: 18px;
              line-height: 18px;
              padding: 0 5px;
              font-size: 12px;
              background: #eee;
              color: #757575;
              margin-right: 5px;
              cursor: pointer;
              &:hover {
                color: #fff;
                background: #ff6300;
              }
            }
          }
        }
        .fadeOut-enter-active, .fadeOut-leave-active {
          transition: all .3s ease;
          opacity: 1;
        }
        .fadeOut-enter, .fadeOut-leave-to {
          opacity: 0;
        }
        >.search-ipt {
          width: 240px;
          height: 100%;
          border: 0;
          outline: none;
        }
        >.search-btn {
          width: 50px;
          height: 100%;
          line-height: 44px;
          border-left: 1px solid #e0e0e0;
          cursor: pointer;
          text-align: center;
          &:hover {
            background: #ff6700;
            .iconfont {
              color: #fff;
            }
          }
          .iconfont {
            font-family:"iconfont" !important;
            font-size: 20px;
            color: #616161;
          }
        }
        >.search-result {
          display: none;
          position: absolute;
          left: -1px;
          top: 50px;
          width: 244px;
          height: auto;
          margin: 0;
          padding: 0;
          list-style: none;
          border: 1px solid #ff6700;
          z-index: 11;
          background: #fff;
          li {
            padding: 7px 13px;
            width: 100%;
            height: 30px;
            display: flex;
            justify-content: space-between;
            box-sizing: border-box;
            cursor: pointer;
            &:hover {
              background: #eee;
            }
            .item-name {
              font-size: 12px;
            }
            .item-num {
              font-size: 10px;
              color: #b0b0b0;
            }
          }
        }
      }
    }
    .fadeIn-enter-active, .fadeIn-leave-active {
      transition: all .3s ease-in;
      height: 230px;
      opacity: 1;
      overflow: hidden;
    }
    .fadeIn-enter, .fadeIn-leave-to {
      height: 0;
      opacity: 0;
    }
    .header-menu {
      position: absolute;
      left: 0;
      top: 140px;
      width: 100%;
      height: 230px;
      background: #fff;
      box-shadow: 0 1px 5px #ccc;
      z-index: 11;
      .menus {
        width: 1226px;
        margin-right: auto;
        margin-left: auto;
        display: flex;
        li {
          position: relative;
          width: 180px;
          padding: 35px 12px 0;
          text-align: center;
          a {
            padding: 0 10px;
            border-right: 1px solid #ccc;
          }
          &:nth-last-child(1) {
            a {
              border-right: 0;
            }
          }
          >.info {
            position: absolute;
            top: -1px;
            left: 0;
            z-index: 1;
            width: 100%;
            font-size: 12px;
            text-align: center;
            .flag {
              display: inline-block;
              height: 18px;
              padding: 1px 20px;
              border: 1px solid #ff6700;
              color: #ff6700;
            }
          }
          >a {
            margin: 5px auto 16px;
            text-align: center;
            border-right: 1px solid #ccc;
            display: inline-block;
            >img {
              width: 160px;
              height: 110px;
            }
          }                
          >.price {
            line-height: 20px;
            color: #ff6700;
          }
          >.name {
            line-height: 20px;
            color: #333;
          }
        }
      }
    }
  }
  
</style>