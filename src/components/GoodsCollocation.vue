<template>
	<div class="around-container">
		<div class="goods-top clearfix">
			<h3 class="top-title">家电</h3>
			<ul class="top-sub">
				<li v-for="sub in subs"
					:class="{'active': topSubStatus === sub.key}"
					@mouseenter="topSubEnter(sub.key)">{{sub.name}}</li>
			</ul>
		</div>
		<div class="goods-content clearfix">
			<goods-left :left-goods="leftGoods"/>
			<goods-right :curr-goods="currGoods"/>
		</div>
	</div>
</template>

<script>
import GoodsTop from './GoodsTop'
import GoodsLeft from './GoodsLeft'
import GoodsRight from './GoodsRight'
export default {
	data () {
		return {
			topTitle: '家电',
			subs: [
				{name: '热门', key: 'hotGoods'},
				{name: '电视影音', key: 'tv'},
				{name: '电脑', key: 'computer'},
				{name: '家居', key: 'home'}
			],
			topSubStatus: 'hotGoods',
			currGoods: [],
			leftGoods: [
				{link: 'https://www.mi.com/air2/', imgUrl: './static/imgs/xmjhq2.jpg'}
			],
			hotGoods: [
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xm4a.png', 'title': '小米电视4A 49英寸',
					price: '2299', oldPrice: '2599', discountType: 'discount', discount: '享九折', heat: '7.1-7.31 直降300',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
				{link: 'https://item.mi.com/buy/mitv4a-43', imgUrl: './static/imgs/xmds4a43.png', 'title': '小米电视4A 43英寸',
					price: '2099', heat: '2GB+8GB 真四核64位高性能处理器',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmbjb13.3.jpg', 'title': '小米笔记本Air 13.3英寸',
					price: '4999', heat: '独立显卡，全金属机身，超长续航',reviewDesc: '是买给老婆的生日礼物！我们一家在我的带领下差不多都是...', reviewAuthor: '纷飞泪', reviewStatus: true},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmbjb12.5.jpg', 'title': '小米笔记本Air 12.5英寸',
					price: '3599',heat: '集成显卡，全金属机身，超长续航',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
				{link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/ddys.jpg', 'title': '米家声波电动牙刷',
					price: '199', discountType: 'new', discount: '新品', heat: '磁悬浮声波马达，定制多种刷牙模式',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/mjdfb.jpg', 'title': '米家压力IH电饭煲',
					price: '999', heat: '智能烹饪，灰铸铁粉体涂层内胆',reviewDesc: '中国人终于可以不要到国外去买电饭煲了！坐在家里点点手...', reviewAuthor: '姚士祥', reviewStatus: true},
				{link: 'https://www.mi.com/yeelight-ceilinglamp/', imgUrl: './static/imgs/mjled.png', 'title': 'Yeelight LED 吸顶灯',
					price: '379', heat: '5分钟快装，月光夜灯，IP60 级防尘',reviewDesc: '可以改变色温，光暗，有一键夜灯，功能强大。本来不懂磁...', reviewAuthor: '冼伟强', reviewStatus: true},
				{ link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/mjsd.jpg', 'title': '米家扫地机器人',
					price: '1699', heat: '5分钟快装，月光夜灯，IP60 级防尘',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
			],
			tv: [
				{link: '//www.mi.com/huosai2/', imgUrl: '//i3.mifile.cn/a4/T1..W_Bvxv1RXrhCrK.jpg', 'title': '小米活塞耳机 基础版',
					price: '29', heat: '5.4万', reviewDesc: '音质非常的好，很震撼！！美美美！', reviewAuthor: '米米小米aa', reviewStatus: true},
				{link: '//www.mi.com/quantie/', imgUrl: '//i1.mifile.cn/a1/T1ycK_BjYv1RXrhCrK!220x220.jpg', 'title': '小米圈铁耳机',
					price: '99', heat: '1.3万', reviewDesc: '客服妹子实话说吧！永远支持国产，永远支持小米。这圈铁...', reviewAuthor: '894039435', reviewStatus: true},
				{link: '//item.mi.com/1161800009.html', imgUrl: '//i1.mifile.cn/a1/T1SkV_BCd_1RXrhCrK!220x220.jpg', 'title': '小米胶囊耳机',
					price: '69', heat: '1.1万', reviewDesc: '很小巧 像不喜欢戴活塞的人可以试试这种~很舒服包装还...', reviewAuthor: '鹤唳', reviewStatus: true},
				{link: '//www.mi.com/bluetooth-tv/', imgUrl: '//i1.mifile.cn/a1/T190DvB4dv1RXrhCrK!220x220.jpg', 'title': '小米蓝牙耳机',
					price: '79', heat: '8.8万', reviewDesc: '东西不错，特别轻，以前买过别的蓝牙耳机，带几天就不带...', reviewAuthor: 'A@然', reviewStatus: true},
				{link: '//www.mi.com/yinxiang/', imgUrl: '//i1.mifile.cn/a1/T1Tfd_BjAv1RXrhCrK!220x220.jpg', 'title': '小米小钢炮蓝牙音箱2',
					price: '129', heat: '1.1万', reviewDesc: '小米节礼券立减50，千值万值啊！物流很快，第二天就到...', reviewAuthor: '潇逸云', reviewStatus: true},
				{link: '//www.mi.com/littleaudio/', imgUrl: '//i1.mifile.cn/a1/T1LqYgBCWv1RXrhCrK!220x220.jpg', 'title': '小米随身蓝牙音箱',
					price: '69', heat: '7513', reviewDesc: '小巧，便携，连接方便还有电量显示！总体很不错，可以挂...', reviewAuthor: '佰亊柒禧', reviewStatus: true},
				{link: '//www.mi.com/pocketaudio/', imgUrl: '//i1.mifile.cn/a1/T1yf__BjAT1RXrhCrK!220x220.jpg', 'title': '小米蓝牙音箱',
					price: '199', oldPrice: '8.8', heat: '1.9万', reviewDesc: '还可以插内存卡，可以插线播放，音质很棒，如果体积大点...', reviewAuthor: '422979039', reviewStatus: true},
				{moreUrl: '//list.mi.com/17', link: '//www.mi.com/speaker/', imgUrl: '//i1.mifile.cn/a1/T15hZ_BsDv1RXrhCrK!220x220.jpg', 'title': '小米小钢炮蓝牙音箱 青春版', price: '99'}
			],
			computer: [
				{link: '//www.mi.com/dianyuan5000/', imgUrl: '//i3.mifile.cn/a4/T1AcE_Bghv1RXrhCrK.jpg', 'title': '移动电源5000mAh',
					price: '49', heat: '8.7万', reviewDesc: '商品非常满意！本来是送给哥哥的！打开包装后太喜欢了！...', reviewAuthor: '296727733', reviewStatus: true},
				{link: '//www.mi.com/dianyuan10000/', imgUrl: '//i1.mifile.cn/a1/T12HJvByEv1RXrhCrK!220x220.jpg', 'title': '移动电源10000mAh',
					price: '79', heat: '19.1万', reviewDesc: '美观小巧，便于携带，希望小米再接再厉！永远支持你！你...', reviewAuthor: '888846438', reviewStatus: true},
				{link: '//www.mi.com/dianyuan10000/pro/', imgUrl: '//i1.mifile.cn/a1/T1eSZgBjVT1RXrhCrK!220x220.jpg', 'title': '移动电源10000mAh 高配版',
					price: '149', heat: '2万', reviewDesc: ' 手感超舒服，有USB C输入充电，以后不用到处换插头了', reviewAuthor: '玻璃樽81', reviewStatus: true},
				{link: '//item.mi.com/1154400042.html', imgUrl: '//i3.mifile.cn/a4/T1x8J_BgEv1RXrhCrK.jpg', 'title': '移动电源20000mAh',
					price: '149', heat: '4.7万', reviewDesc: '一如既往的好评！支持小米！', reviewAuthor: '小丹555', reviewStatus: true},
				{link: '//item.mi.com/1152000009.html', imgUrl: '//i1.mifile.cn/a1/T1vSDQB4_T1RXrhCrK!220x220.jpg', 'title': '10000mAh小米移动电源保护套',
					price: '19.9', heat: '2万', reviewDesc: '可好了，能有效的保护手机了，再也不用担心移动电源被磨...', reviewAuthor: '682837881', reviewStatus: true},
				{link: '//www.mi.com/computerstrip/', imgUrl: '//i3.mifile.cn/a4/T1jMbjB5Jv1RXrhCrK.jpg', 'title': '小米插线板（3孔位+USB）',
					price: '49', heat: '24.7万', reviewDesc: '做工沒的說，摸起來手感非常細膩，而且比起傳統的插線板...', reviewAuthor: '林岐城', reviewStatus: true},
				{link: '//www.mi.com/chongdianqi4kou/', imgUrl: '//i1.mifile.cn/a1/T1vFEjBbWT1RXrhCrK!220x220.jpg', 'title': '小米USB充电器（4口）',
					price: '69', oldPrice: '8.8', heat: '7051', reviewDesc: '挺不错哒小巧精致非常使用，支持快充', reviewAuthor: '朋哥441035', reviewStatus: true},
				{moreUrl: '//list.mi.com/11', link: '//item.mi.com/1154500022.html', imgUrl: '//i3.mifile.cn/a4/T1Ihd_BTCv1RXrhCrK.jpg', 'title': '小米插线板 5孔位', price: '39'}
			],
			home: [
				{link: '//item.mi.com/1134900527.html', imgUrl: '//i1.mifile.cn/a1/T1sRhTBsYT1RXrhCrK!220x220.jpg', 'title': 'SanDisk 16GB存储卡（Class4）',
					price: '26.9', heat: '7.9万', reviewDesc: '物美价廉，正品行货，发货迅速', reviewAuthor: 'sharph', reviewStatus: true},
				{link: '//item.mi.com/1153300072.html', imgUrl: '//i1.mifile.cn/a1/T1ipAvB_ZT1RXrhCrK!220x220.jpg', 'title': '原装快充套装', discountType: 'discount', discount: '享八折',
					price: '58', oldPrice: '78', heat: '0', reviewDesc: '客服妹子实话说吧！永远支持国产，永远支持小米。这圈铁...', reviewAuthor: '894039435', reviewStatus: true},
				{link: '//item.mi.com/1154300033.html', imgUrl: '//i1.mifile.cn/a1/T1xxVTBghv1RXrhCrK!220x220.jpg', 'title': '彩虹5号电池（10粒装）',
					price: '9.9', heat: '6.9万', reviewDesc: '价格实惠，外观好看，还有盒子便于保管，不错。', reviewAuthor: 'monkeyshine', reviewStatus: true},
				{link: '//item.mi.com/1155000010.html', imgUrl: '//i1.mifile.cn/a1/T178EjBjVT1RXrhCrK!220x220.jpg', 'title': '彩虹7号电池（10粒装）',
					price: '9.9', heat: '4万', reviewDesc: '好用，好看。。价格实惠', reviewAuthor: '米米徳', reviewStatus: true},
				{link: '//item.mi.com/1151400067.html', imgUrl: '//i1.mifile.cn/a1/T16XAgB5dT1RXrhCrK!220x220.jpg', 'title': 'CR2032纽扣电池',
					price: '9', heat: '1.3万', reviewDesc: '小米把关，质量还是有得保证的，暂时还没用，先备着！', reviewAuthor: '陶都', reviewStatus: true},
				{link: '//www.mi.com/recharger/', imgUrl: '//i3.mifile.cn/a4/T1gVCgBjDv1RXrhCrK.jpg', 'title': '紫5镍氢充电电池',
					price: '49', heat: '2367', reviewDesc: '终于出了充电电池，外形时尚，喜欢', reviewAuthor: '吴国立', reviewStatus: true},
				{link: '//item.mi.com/1154400043.html', imgUrl: '//i1.mifile.cn/a1/T142A_BXEv1RXrhCrK!220x220.jpg', 'title': '小米车载充电器',
					price: '49', oldPrice: '8.8', heat: '3万', reviewDesc: '很好，个头小能量大，很满意', reviewAuthor: '你再猜猜啊', reviewStatus: true},
				{moreUrl: '//list.mi.com/135', link: '//item.mi.com/1152400014.html', imgUrl: '//i1.mifile.cn/a1/T1_lKvBKZT1RXrhCrK!220x220.jpg', 'title': '红米2/红米2A能量套装', price: '69'}
			]
		}
	},
	mounted(){ //Vue2.0 替换了之前的ready，详见文档生命周期函数mounted
    this.currGoods = this.hotGoods
  },
	methods: {
		topSubEnter (key) {
			this.topSubStatus = key
			this.currGoods = this[key]
		}
	},
	components: {
		'goods-top': GoodsTop,
		'goods-left': GoodsLeft,
		'goods-right': GoodsRight
	}
}
</script>

<style scoped lang="scss">
	.around-container {
		width: 1226px;
		height: auto;
		margin: 0 auto;
		background: #f5f5f5;
		>.goods-top {
			width: 100%;
			height: 58px;
			.top-title {
				float: left;
				margin: 0;
				font-size: 22px;
				font-weight: 200;
				line-height: 58px;
				color: #333;
			}
			.top-sub {
				float: right;
				display: flex;
				flex-flow: row nowrap;
				justify-content: flex-start;
				align-items: center;
				font-size: 16px;
				margin-top: 16px;
				color: #424242;
				li {
					width: auto;
					height: 24px;
					line-height: 24px;
					margin-left: 30px;
					cursor: pointer;
					border-bottom: 2px solid #f5f5f5;
					&.active {
						color: #ff6700;
						border-bottom: 2px solid #ff6700;
					}
				}
			}
		}
	}
.goods-content {
	width: 1226px;
	height: auto;
	margin: 0 auto;
}
</style>
