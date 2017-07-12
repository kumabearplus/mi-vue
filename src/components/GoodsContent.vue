<template>
	<div class="product-container">
		<h2 class="title">{{title}}</h2>
		<div class="box-bd">
			<ul class="content-list clearfix">
				<li>
					<template v-for="content in contents">
						<good-content-slide :content="content"></good-content-slide>
					</template>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>

import GoodsContentSlide from './GoodsContentSlide'

export default {
	data () {
		return {
			currPage: 0,
			title: '内容',
			contents: [
				{
					title: '图书',
					type: 'book',
					length: 3,
					list: [
						{link: 'http://www.duokan.com/book/115222', title: '哈利·波特与被诅咒的孩子', desc: '“哈利·波特”第八个故事中文版震撼来袭！特别彩排版剧本！ ', imgUrl: './static/imgs/hlbt.png', price: '29.37元', type: 1},
						{link: 'http://www.duokan.com/book/115222', title: '好吗好的', desc: '畅销作家大冰2016年新书！讲给你听，好吗好的！', imgUrl: './static/imgs/hmhd.png', price: '17.99元', type: 1},
						{link: 'http://www.duokan.com/list/1-1?from=xiaomi', desc1: '海量好书，享受精品阅读时光', desc2: '漂亮的中文排版，千万读者选择！', btnTxt: '前往多看阅读', imgUrl: './static/imgs/more-duokan.jpg', type: 2}
					]
				},
				{
					title: 'MIUI主题',
					type: 'theme',
					length: 4,
					list: [
						{link: 'http://zhuti.xiaomi.com/detail/4ecf4ebb-7cba-4142-96aa-6b8deb2426ef', title: '夏日狂想', desc: '官方主题新画风，原来你是这样的小清新！', price: '免费', imgUrl: './static/imgs/xrkx.jpg', type: 1},
						{link: 'http://zhuti.xiaomi.com/detail/d6277519-ca46-420c-ab09-060f6d293f94', title: '几何', desc: '最新官方主题，带你感受极简视觉冲击', price: '免费', imgUrl: './static/imgs/jh.jpg', type: 1},
						{link: 'http://zhuti.xiaomi.com/detail/13df18d4-e52c-4a61-82e3-97014f21bd77', title: '几何·简黑', desc: '最新官方主题，带你感受极简视觉冲击，简黑版更加酷炫', price: '免费', imgUrl: './static/imgs/jhjh.jpg', type: 1},
						{link: 'http://zhuti.xiaomi.com/?from=mi', desc1: '众多个性主题、百变锁屏与自由桌面', desc2: '让你的手机与众不同！', btnTxt: '前往MIUI主题市场', imgUrl: './static/imgs/more-miui.jpg', type: 2}
					]
				},
				{
					title: '游戏',
					type: 'game',
					length: 3,
					list: [
						{link: 'http://ljm.mi.com/?channel=meng_1084_1_android', title: '米柚手游模拟器', desc: '在电脑上玩遍小米所有手游', price: '免费', imgUrl: './static/imgs/mysymlq.png', type: 1},
						{link: 'http://game.xiaomi.com/miyou/index.html', title: '剑侠世界', desc: '一生不容错过的浪漫武侠！！', price: '免费', imgUrl: './static/imgs/jssj.jpg', type: 1},
						{link: 'http://game.xiaomi.com/index.php?c=index&a=run', desc1: '免费下载海量的手机游戏', desc2: '天天都有现金福利赠送', btnTxt: '前往小米游戏商店', imgUrl: './static/imgs/more-game.jpg', type: 2}
					]
				},
				{
					title: '应用',
					type: 'app',
					length: 4,
					list: [
						{link: 'http://app.mi.com/subject/168797', title: '2017金米奖', desc: '最优秀的应用和游戏', imgUrl: './static/imgs/2017jmj.png', type: 0},
						{link: 'http://app.mi.com/subject/168798', title: 'Forest', desc: '帮助您专心于生活中每个重要时刻', price: '免费', imgUrl: './static/imgs/forest.png', type: 1},
						{link: 'http://app.mi.com/subject/167924', title: '小米应用', desc: '小米出品 必属精品', price: '免费', imgUrl: './static/imgs/xmyyong.png', type: 1},
						{link: 'http://app.mi.com/?from=mi', desc1: '帮助小米手机和其他安卓手机用户', desc2: '发现好用的安卓应用', btnTxt: '前往小米应用商店', imgUrl: './static/imgs/more-app.jpg', type: 2}
					]
				}]
		}
	},
	components: {
		'good-content-slide': GoodsContentSlide
	}
}
</script>

<style scoped lang="scss">
.product-container {
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
</style>
