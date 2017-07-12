<template>
	<div class="hot-container">
		<h2 class="title">{{title}}</h2>
		<div class="hot-wrap">
			<ul class="hot-content clearfix">
				<li class="hot-item"
					v-for="item in hots">
					<a :href="item.link" target="_blank">
						<img class="item-image" :src="item.imgUrl" alt="" />
						<div class="item-evaluation">
							<p class="review-txt">{{item.review}}</p>
							<p class="author">来自 {{item.author}} 的评价</p>
						</div>
						<div class="item-desc">
							<span class="item-name">{{item.name}}</span>
							<span class="sep">|</span>
							<span class="item-price">{{item.price}}元</span>
						</div>
					</a>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>

export default {
	data () {
		return {
			title: '热评产品',
			hots: [
				{link: 'http://item.mi.com/buymibook/air', imgUrl: './static/imgs/xmbk12.5.jpg', review: '刚收到，外观很漂亮，颜色也很喜欢，等了好长时间了，终于拿到了，非常满意，棒棒哒！！！', author: '龙炎', name: '小米笔记本Air 12.5英寸', price: '3499'},
				{link: 'http://item.mi.com/buymibook/air', imgUrl: './static/imgs/dfbpj.jpg', review: '包装很让人感动，式样也很可爱，做出的饭全家人都爱吃，超爱五星！手机控制还是不太熟练，最主要是没有连接...', author: 'HZG', name: '米家压力IH电饭煲', price: '999'},
				{link: 'http://item.mi.com/buymibook/air', imgUrl: './static/imgs/lxx.jpg', review: '这箱子很好，外观漂亮，实用性强。很轻，有点软但不影响它的坚固。', author: '子书雁', name: '90分旅行箱 20寸', price: '269'},
				{link: 'http://item.mi.com/buymibook/air', imgUrl: './static/imgs/mtgsj.jpg', review: '非常可爱，一拿到小宝宝还没享受，一帮大宝宝先high了一把，同事也想买，希望早点大卖', author: '秘密', name: '米兔智能故事机', price: '199'}
			]
		}
	}
}
</script>

<style scoped lang="scss">
.hot-container {
	width: 1226px;
	height: auto;
	margin: 0 auto;
	.title {
		margin: 0;
		font-size: 22px;
		font-weight: 200;
		line-height: 58px;
		color: #333;
	}
}

.hot-header {
	position: relative;
	.title {
		margin: 0;
		font-size: 22px;
		font-weight: 200;
		line-height: 58px;
		color: #333;
	}
}

.hot-wrap {
	position: relative;
}

.hot-content {
	.hot-item {
		float: left;
		width: 296px;
		height: 415px;
		margin: 0 0 14px 14px;
		cursor: pointer;
		transition: all 0.3s;
		background: #fff;
		&:nth-child(1) {
			margin-left: 0;
		}
		&:hover {
			transform: translateY(-3px);
			box-shadow: 5px 5px 20px #ccc;
		}
		.item-image {
			width: 296px;
			height: 220px;
		}
		.review-txt {
			height: 72px;
			margin: 22px 28px;
			font-size: 14px;
			line-height: 24px;
			font-weight: 400;
			overflow: hidden;
		}
		.author {
			position: relative;
			height: 18px;
			margin: 0 28px 8px;
			padding: 0 10px 0 0;
			font-size: 12px;
			color: #b0b0b0;
		}
	}
}

.item-desc {
	padding-left: 30px;
	.item-name {
		font-size: 14px;
		color: #333;
	}
	.sep {
		margin: 0 4px;
		color: #e0e0e0;
	}
	.item-price {
		font-size: 14px;
		color: #ff6700;
	}
}

</style>
