<template>
	<div class="recommend-container">
		<div class="recommend-header">
			<h2 class="title">为你推荐</h2>
			<div class="control-part">
				<span
					@click="slidePre"
					class="control control-left"
					:class="{'disable': this.currPage2 === 0}">
					<i class="iconfont">&#xe621;</i>
				</span>
				<span
					@click="slideNext"
					class="control control-right"
					:class="{'disable': this.currPage2 === Math.floor((this.recomends.length - 1) / 5)}">
					<i class="iconfont">&#xe606;</i>
				</span>
			</div>
		</div>
		<div class="recommend-wrap">
			<ul class="recommend-content clearfix">
				<li class="recomend-item"
					v-for="item in recomends">
					<a :href="item.link">
						<img class="item-image" :src="item.imgUrl" :alt="item.name">
					</a>
					<h3 class="title">
						<a :href="item.link">{{item.name}}</a>
					</h3>
					<p class="price">{{item.price}}</p>
					<p class="favorable" v-show="item.favorStatus">
						{{item.favorable}}
					</p>
					</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>

import $ from 'jquery'

export default {
	name: 'Recommend',
	data () {
		return {
			currPage2: 0,
			recomends: [
				{link: 'http://item.mi.com/1163900098.html', imgUrl: './static/imgs/xmds65.jpg', name: '小米电视3s 65英寸 影院版', price: '6499元', favorable: '',favorStatus: false},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/ydsb.jpg', name: 'Amazfit 运动手表', price: '799元', favorable: '   5718人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/mjxcjly.jpg', name: '米家行车记录仪', price: '329元', favorable: '   6373人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/mjddhb.jpg', name: '小米米家电动滑板车', price: '1999元', favorable: '   2164人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmydlyej.jpg', name: '小米运动蓝牙耳机', price: '139元', favorable: '   1万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmyd2.jpg', name: '10000mAh小米移动电源2', price: '79元', favorable: '   4.6万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xxetsb.jpg', name: '小寻儿童电话手表 彩屏版', price: '199元', favorable: '   2882人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmlyq.jpg', name: '小米路由器 HD', price: '1299元', favorable: '    613人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmvr2.jpg', name: '小米VR眼镜PLAY2', price: '99元', favorable: '      593人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/mjydxnk.jpg', name: '米家运动鞋(智能版) 女款', price: '229元', favorable: '   1601人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/yddy.jpg', name: '小米移动电源10000mAh高配版', price: '129元', favorable: '   8254人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmwlyx.jpg', name: '小米网络音响', price: '349元', favorable: '      6192人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmhsej.jpg', name: '小米活塞耳机 清新版', price: '29元', favorable: '   4.6万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmlyejqc.jpg', name: '小米蓝牙耳机青春版', price: '59元', favorable: '   2.8万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmjtyy.jpg', name: '小米家庭影院', price: '1999元', favorable: '   5718人好评    ',favorStatus: false},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/90flxx.jpg', name: '90分旅行箱 20寸', price: '269元', favorable: '   2.3万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/90f24lxx.jpg', name: '90分旅行箱 20寸', price: '269元', favorable: '   2.3万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmcxb.jpg', name: '小米插线板（含3口USB 2A快充）', price: '49元', favorable: '   28.5万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/xmxgp.jpg', name: '小米小钢炮蓝牙音箱2', price: '129元', favorable: '   2.7万人好评    ',favorStatus: true},
				{link: 'http://item.mi.com/1164300010.html', imgUrl: './static/imgs/mtjmjqr.jpg', name: '米兔积木机器人', price: '459元', favorable: '   4321人好评    ',favorStatus: true}
			]
		}
	},
	methods: {
		slideNext () {
			if (this.currPage2 < Math.floor((this.recomends.length - 1) / 5)) {
				this.currPage2++
				$('.recommend-content').css('margin-left', this.currPage2 * (-1224) + 'px')
			}
		},
		slidePre () {
			if (this.currPage2 !== 0) {
				this.currPage2--
				$('.recommend-content').css('margin-left', this.currPage2 * (-1224) + 'px')
			}
		}
	}
}
</script>

<style scoped lang="scss">
	.iconfont {
	  font-family:"iconfont" !important;
	  color: #b0b0b0;
    font-size: 10px;
	  font-style:normal;
	  -webkit-font-smoothing: antialiased;
	  -moz-osx-font-smoothing: grayscale;
	}
	.recommend-container {
		width: 1226px;
		height: auto;
		margin: 0 auto;
		padding-bottom: 40px;
		>.recommend-header {
			position: relative;
			.title {
				margin: 0;
				font-size: 22px;
				font-weight: 200;
				line-height: 58px;
				color: #333;
			}
			.control-part {
				position: absolute;
				top: 10px;
				right: 0;
				float: left;
				display: block;
				.control {
					display: block;
					float: left;
					width: 34px;
					height: 23px;
					line-height: 23px;
					text-align: center;
					border: 1px solid #e0e0e0;
					cursor: pointer;
					&:hover {
						.iconfont {
							color: #ff6700;
						}
					}
					&.disable {
						&:hover {
							.iconfont {
								color: #e0e0e0;
							}
						}
						.iconfont {
							color: #e0e0e0;
						}
					}
					.iconfont {
						color: #b0b0b0;
						font-size: 10px;
					}
				}
			}
		}
		>.recommend-wrap {
			width: 1226px;
			height: 340px;
			overflow: hidden;
			>.recommend-content {
				width: auto;
				height: 340px;
				transition: all 0.3s;
				.recomend-item {
					float: left;
					display: block;
					height: 300px;
					width: 234px;
					margin-right: 14px;
			    padding-top: 39px;
			    border-top-width: 1px;
			    border-top-style: solid;
			    text-align: center;
			    background: #fff;
			    -webkit-transition: all .6s;
			    transition: all .6s;
					>a {
						display: block;
				    width: 140px;
				    margin: 0 auto 22px;
				    >.item-image {
							width: 140px;
				    	height: 140px;
						}
					}
					>.title {
						margin-bottom: 10px;
				    font-size: 14px;
				    font-weight: 400;
				    text-overflow: ellipsis;
				    white-space: nowrap;
				    overflow: hidden;
				    >a {
				    	color: #212121;
				    }
					}
					>.favorable {
						height: 18px;
				    color: #757575;
					}
					>.price {
						margin-bottom: 10px;
			    	color: #ff6709;
					}
					&:nth-child(5n+1) {
						border-top-color: #ffac13;
					}
					&:nth-child(5n+2) {
						border-top-color: #83c44e;
					}
					&:nth-child(5n+3) {
						border-top-color: #2196f3;
					}
					&:nth-child(5n+4) {
						border-top-color: #e53935;
					}
					&:nth-child(5n) {
						margin-right: -3px;
						border-top-color: #00c0a5;
					}	
				}
			}
		}
	}
</style>
