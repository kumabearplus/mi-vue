<template>
  <div id="top-sub">
		<div class="sub-1">
      <ul  class="channels">
        <li v-for="channel in channels" class="channel">
          <a :href="channel.link">
            <svg class="iconfont" aria-hidden="true">
                <use :xlink:href="`#icon-${channel.icon}`"></use>
            </svg>
            <span class="channel-txt">{{channel.name}}</span>
          </a>
        </li>
      </ul>
<!-- 			<ul class="channels">
				<li class="channel">
          <a href="http://www.mi.com/compare/" target="_blank">
  					<span class="iconfont">&#xe603;</span>
            <span class="channel-txt">
              选购手机
            </span>
          </a>
				</li>
				<div class="line-vertical">
				</div>
				<li class="channel">
          <a href="http://qiye.mi.com/" target="_blank">
  					<span class="iconfont">&#xe604;</span>
            <span class="channel-txt">
              企业团购
            </span>
          </a>
				</li>
				<div class="line-vertical">
				</div>
				<li class="channel">
          <a href="http://item.mi.com/re" target="_blank">
  					<span class="iconfont">&#xe72c;</span>
            <span class="channel-txt">
              一元活动
            </span>
          </a>
				</li>
				<div class="line-horizontal">
				</div>
				<div class="line-horizontal">
				</div>
				<div class="line-horizontal">
				</div>
				<li class="channel">
          <a href="http://huanxin.mi.com/product/list" target="_blank">
  					<span class="iconfont">&#xe605;</span>
            <span class="channel-txt">
              小米移动
            </span>
          </a>
				</li>
				<div class="line-vertical">
				</div>
				<li class="channel">
          <a href="http://huanxin.mi.com/product/list" target="_blank">
  					<span class="iconfont">&#xe601;</span>
            <span class="channel-txt">
              以旧换新
            </span>
          </a>
				</li>
				<div class="line-vertical">
				</div>
				<li class="channel">
          <a href="http://recharge.10046.mi.com/" target="_blank">
  					<span class="iconfont">&#xe602;</span>
            <span class="channel-txt">
              话费充值
            </span>
          </a>
				</li>
			</ul> -->
		</div>
    <div class="subs">
      <ul class="sales">
        <li v-for="sale in sales">
          <a :href="sale.link" class="sub-item">
            <img :src="sale.imgUrl">
          </a>
        </li>
      </ul>
    </div>
		<!-- <ul class="subs">
			<li>
				<a href="https://item.mi.com/product/10000029.html" class="sub-item sub-2" target="_blank">
					<img src="../../static/imgs/xmad-hm4x.jpg" alt="">
				</a>
			</li>
			<li>
				<a href="https://a.union.mi.com/mua?c=10292.0002" class="sub-item sub-3" target="_blank">
          <img src="../../static/imgs/xmad-xm5c.jpg" alt="">
				</a>
			</li>
			<li>
				<a href="https://list.mi.com/accessories/tag?id=yinpin" class="sub-item sub-4" target="_blank">
					<img src="../../static/imgs/xmad-xmyp.jpg" alt="">
				</a>
			</li>
		</ul> -->
	</div>
</template>

<script>
export default {
	data () {
		return {
      channels: [
        {name:'选购手机',icon:'xuangoushouji',link:'https://www.mi.com/compare/'},
        {name:'企业团购',icon:'liwu',link:'http://qiye.mi.com/'},
        {name:'一元活动',icon:'lanmaofenleiyiyuangou',link:'https://1.hd.mi.com/'},
        {name:'小米移动',icon:'tubiaozhizuomoban',link:'https://www.mi.com/mimobile/'},
        {name:'以旧换新',icon:'yijiuhuanxin',link:'https://huanxin.mi.com/'},
        {name:'话费充值',icon:'shoujichongzhixian',link:'http://recharge.10046.mi.com/'}
      ],
      sales: [
        {link:'https://item.mi.com/product/10000029.html',imgUrl:'./static/imgs/xmad-hm4x.jpg'},
        {link:'https://a.union.mi.com/mua?c=10292.0002',imgUrl:'./static/imgs/xmad-xm5c.jpg'},
        {link:'https://list.mi.com/accessories/tag?id=yinpin',imgUrl:'./static/imgs/xmad-xmyp.jpg'}
      ]
		}
	}
}
</script>

<style scoped lang="scss">
  @font-face {
    font-family: 'iconfont';  /* project id 345452 */
    src: url('//at.alicdn.com/t/font_523pdcq6aiz4cxr.eot');
    src: url('//at.alicdn.com/t/font_523pdcq6aiz4cxr.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_523pdcq6aiz4cxr.woff') format('woff'),
    url('//at.alicdn.com/t/font_523pdcq6aiz4cxr.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_523pdcq6aiz4cxr.svg#iconfont') format('svg');
  }

  #top-sub {
  	position: relative;
  	width: 1226px;
  	height: auto;
  	margin: 14px auto 26px;
    >.sub-1 {
      float: left;
      width: 234px;
      height: 170px;
      background: #5f5750;
      >.channels {
        display: flex;
        flex-flow: wrap;
        justify-content: flex-start;
        align-items: flex-start;
        padding: 3px;
        .channel {
          width: 75px;
          height: 82px;
          padding-top: 15px;
          padding-bottom: 15px;
          box-sizing: border-box;
          cursor: pointer;
          &:hover{
            .channel-txt {
              color: #fff;
            }
            .iconfont {
              color: #fff;
              fill: #fff;
            }
          }
          .channel-txt {
            display: block;
            width: 75px;
            font-size: 12px;
            text-align: center;
            text-decoration: none;
            color: rgba(255,255,255,0.7);
          }
          .iconfont {
            font-family:"iconfont" !important;
            font-style:normal;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            display: block;
            height: 24px;
            width: 75px;
            fill: rgba(255, 255, 255, 0.7);
            margin-bottom: 4px;
            font-size: 24px;
            line-height: 24px;
            text-align: center;
            color: rgba(255, 255, 255, 0.7);
          }
        }
      }
    }
    .sales {
      display: flex;
      flex-flow: row nowrap;
      justify-content: flex-start;
      li {
        width: 316px;
        height: 170px;
        margin-left: 15px;
      }
      .sub-item {
        display: block;
        transition: all 0.3s;
        &:hover {
          box-shadow: 0 5px 30px #ccc;
        }
        img {
          display: block;
          width: 316px;
          height: 170px;
        }
      }
    }
  }
  .line-vertical {
  	width: 1px;
  	height: 60px;
  	margin-top: 10px;
  	background: rgba(255,255,255,0.1);
  }

  .line-horizontal {
  	width: 60px;
  	height: 1px;
  	margin: 0 8px;
  	background: rgba(255,255,255,0.1);
  }
</style>
