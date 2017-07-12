<template>
	<div class="recommend-container">
		<div class="recommend-header">
			<h2 class="title">小米明星单品</h2>
			<div class="control-part">
				<span
					@click="playPre"
					class="control control-left"
					:class="{'disable': this.currPage === 0}">
					<i class="iconfont">&#xe621;</i>
				</span>
				<span
					@click="playNext"
					class="control control-right"
					:class="{'disable': this.currPage === 1}">
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
					<p class="description">{{item.description}}</p>
					<p class="price">{{item.price}}</p>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>

import $ from 'jquery'

export default {
	data () {
		return {
			currPage: 0,
			timeId: '',
			recomends: [
				{link: 'http://item.mi.com/product/10000024.html', imgUrl: './static/imgs/xm5s-64g.png', name: '小米5s 64GB', price: '1999元', description: '“暗夜之眼”超感光相机'},
				{link: 'http://item.mi.com/product/10000025.html', imgUrl: './static/imgs/xm5sp.png', name: '小米5s Plus', price: '2299元起', description: '5.7" 大屏双摄像头，轻薄金属机身'},
				{link: 'http://item.mi.com/product/10000022.html', imgUrl: './static/imgs/xmmix.png', name: '小米MIX', price: '3499元起', description: '6.4" 全面屏，全陶瓷机身'},
				{link: 'http://item.mi.com/buy/mitv4a-49', imgUrl: './static/imgs/xmds4a_49.png', name: '小米电视4A 49英寸 标准版', price: '2299元', description: '直降300元，全高清HDR '},
				{link: 'http://item.mi.com/product/10000032.html', imgUrl: './static/imgs/xmbjb.png', name: '小米笔记本', price: '3599元起', description: '更轻更薄，像杂志一样随身携带'},
				{link: 'http://www.mi.com/battery2/', imgUrl: './static/imgs/xmyddy.png', name: '10000mAh小米移动电源2', price: '79元', description: '双向快充，高密度锂聚合物电芯'},
				{link: 'http://www.mi.com/shouhuan2/', imgUrl: './static/imgs/xmsh.png', name: '小米手环 2', price: '149元', description: 'OLED 显示屏幕，升级计步算法'},
				{link: 'http://www.mi.com/dianfanbao/', imgUrl: './static/imgs/xmdfb.jpg', name: '米家压力IH电饭煲', price: '999元', description: '智能烹饪，压力IH加热技术'},
				{link: 'http://item.mi.com/1164300033.html', imgUrl: './static/imgs/mjjhq.png', name: '米家空气净化器Pro', price: '1499元', description: 'OLED显示屏幕，激光颗粒物传感器'},
				{link: 'http://www.mi.com/miwifi3/', imgUrl: './static/imgs/xmwf.png', name: '小米路由器3', price: '149元', description: '更快更强，不止四天线'}
				
			]
		}
	},
	mounted(){ //Vue2.0 替换了之前的ready，详见文档生命周期函数mounted
    this.autoPlay()
  },
	methods: {
		playNext () {
			if (this.currPage == 0) {
				this.currPage++
				$('.recommend-content').css('margin-left', this.currPage * (-1224) + 'px')
			}
		},
		playPre () {
			if (this.currPage == 1) {
				this.currPage--
				$('.recommend-content').css('margin-left', this.currPage * (-1224) + 'px')
			}
		},
		autoPlay(){
      clearInterval(this.timeId)
      this.timeId = setInterval(()=>{
      	if (this.currPage == 0) {
      		this.playNext()
      	} else if (this.currPage == 1) {
      		this.playPre()
      	}
        
      }, 6000)
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
			    background: #fafafa;
			    -webkit-transition: all .6s;
			    transition: all .6s;
					>a {
						display: block;
				    width: 160px;
				    margin: 0 auto 22px;
				    >.item-image {
							width: 160px;
				    	height: 160px;
						}
					}
					>.title {
						margin: 0 20px 3px;
				    font-size: 14px;
				    font-weight: 400;
				    text-overflow: ellipsis;
				    white-space: nowrap;
				    overflow: hidden;
				    >a {
				    	color: #212121;
				    }
					}
					>.description {
						height: 18px;
				    margin: 0 20px 12px;
				    font-size: 12px;
				    text-overflow: ellipsis;
				    white-space: nowrap;
				    overflow: hidden;
				    _zoom: 1;
				    color: #b0b0b0;
					}
					>.price {
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
						margin-right: -1px;
						border-top-color: #00c0a5;
					}	
				}
			}
		}
	}
</style>
