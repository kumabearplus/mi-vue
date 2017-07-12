<template>
	<div class="video-container">
		<div class="header clearfix">
			<h2 class="title">{{title}}</h2>
			<a href="//www.mi.com/video/" target="_blank">
				<span class="top-sub">
					查看全部
					<i class="iconfont">&#xe606;</i>
				</span>
			</a>
		</div>
		<div class="video-content">
			<ul class="video-wrap clearfix">
				<li class="video-item"
					v-for="item in videos">
					<div class="item-top">
						<img :src="item.imgUrl" alt="" />
						<span class="play">
							<i class="iconfont">&#xe64a;</i>
						</span>
					</div>
					<h3 class="video-title">{{item.title}}</h3>
					<p class="video-desc">
						{{item.desc}}
					</p>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
export default {
	data () {
		return {
			title: '视频',
			videos: [{
				videoUrl: 'http://hd.mi.com/f/zt/hd/misc/youku.html?vid=XMTY1ODg5ODA0MA==',
				imgUrl: './static/imgs/7ngy.jpg',
				title: '听雷总讲述小米7年工艺探索之路',
				desc: '小米6，7年工艺探索的巅峰之作'
			},
			{
				videoUrl: 'http://hd.mi.com/f/zt/hd/misc/youku.html?vid=XMTY1OTg3NjQ4OA==',
				imgUrl: './static/imgs/xm6sp.jpg',
				title: '小米6外观设计视频',
				desc: '震惊！小米6竟然如此之美'
			},
			{
				videoUrl: 'http://hd.mi.com/f/zt/hd/misc/youku.html?vid=XMTY1OTg4NjY0OA==',
				imgUrl: './static/imgs/xm4sp.jpg',
				title: '小米电视4 外观设计视频',
				desc: '美哭了！史上最美的小米电视'
			},
			{
				videoUrl: 'http://hd.mi.com/f/zt/hd/misc/youku.html?vid=XMTU2NDM3NjEzMg==',
				imgUrl: './static/imgs/cbds.jpg',
				title: '4.9mm极超薄电视的诞生揭秘',
				desc: '小米电视工程师讲述极致之作的背后故事'
			}]
		}
	}
}
</script>

<style scoped lang="scss">
	.iconfont {
	  font-family:"iconfont" !important;
    width: 12px;
    height: 12px;
    padding: 4px;
    margin-left: 8px;
    border-radius: 16px;
    font-size: 10px;
    line-height: 12px;
    background: #b0b0b0;
    color: #fff;
    vertical-align: 1px;
    -webkit-transition: all .4s;
    transition: all .4s;
	  font-style:normal;
	  -webkit-font-smoothing: antialiased;
	  -moz-osx-font-smoothing: grayscale;
	}
.video-container {
	width: 1226px;
	height: auto;
	margin: 0 auto;
}
.header {
	position: relative;
	.title {
		display: block;
		float: left;
		margin: 0;
		font-size: 22px;
		font-weight: 200;
		line-height: 58px;
		color: #333;
	}
	.top-sub {
	  float: right;
	  display: block;
	  font-size: 16px;
	  line-height: 58px;
	  color: #424242;
	  cursor: pointer;
	  .iconfont {
	    color: #fff;
	  }
	  &:hover {
	    color: #ff6700;
	    .iconfont {
	      background: #ff6700;
	    }
	  }
	}
}

.video-wrap {
	.video-item {
		position: relative;
		float: left;
		width: 296px;
		height: 285px;
		margin: 0 0 14px 14px;
		background: #fff;
		cursor: pointer;
		transition: all 0.3s;
		&:hover {
			transform: translateY(-3px);
			box-shadow: 5px 5px 20px #ccc;
			.play {
				background: #ff6700;
			}
		}
		&:nth-child(1) {
			margin-left: 0;
		}
		img {
			width: 296px;
			height: 180px;
		}
		.video-title {
			margin: 0 0 6px;
	    font-size: 14px;
	    font-weight: 400;
	    text-align: center;
	    color: #333;
		}
		.video-desc {
			height: 18px;
	    margin: 0;
	    font-size: 12px;
			text-align: center;
	    color: #b0b0b0;
		}
	}
}

.item-top {
  position: relative;
  width: 296px;
  height: 180px;
  margin: 0 0 28px;
	.play {
		position: absolute;
		display: block;
		left: 20px;
		bottom: 10px;
		width: 32px;
		height: 20px;
		line-height: 20px;
		color: #fff;
		text-align: center;
		font-size: 12px;
		border: 2px solid #fff;
		border-radius: 12px;
		background: #333;
		.iconfont {
			background: rgba(0,0,0,0);
			margin: 0;
			padding: 0;
			font-size: 10px;
			width: 30px;
			height: 30px;
			line-height: 20px;
		}
	}
}
</style>
