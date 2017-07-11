<template>
	<div class="around-container">
		<div class="goods-top clearfix">
			<h3 class="top-title">搭配</h3>
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
import GoodsRight from './GoodsRight2'
export default {
	data () {
		return {
			topTitle: '搭配',
			subs: [
				{name: '热门', key: 'hotGoods'},
				{name: '耳机音箱', key: 'headset'},
				{name: '电源', key: 'power'},
				{name: '电池存储卡', key: 'card'}
			],
			topSubStatus: 'hotGoods',
			currGoods: [],
			leftGoods: [
				{link: 'http://www.mi.com/bluetooth-audio/', imgUrl: './static/imgs/lyypjsq.jpg'},
				{link: 'http://www.mi.com/battery20000/', imgUrl: './static/imgs/xmyddy2.jpg'}
			],
			hotGoods: [
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmydlyej.jpg', 'title': '小米运动蓝牙耳机',
					price: '149', heat: '1万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
				{link: 'https://item.mi.com/buy/mitv4a-43', imgUrl: './static/imgs/xmyddy.jpg', 'title': '20000mAh小米移动电源2',
					price: '149', heat: '1.7万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/yddy.jpg', 'title': '小米移动电源10000mAh高配版',
					price: '149', heat: '8206人评价',reviewDesc: '是买给老婆的生日礼物！我们一家在我的带领下差不多都是...', reviewAuthor: '纷飞泪', reviewStatus: true},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmhsej.jpg', 'title': '小米活塞耳机 清新版',
					price: '29',heat: '4.6万人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
				{link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/xmwlyx.jpg', 'title': '小米网络音响',
					price: '349', oldPrice: '399', discountType: 'discount', discount: '享9折', heat: '6154人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/xmlyejqc.jpg', 'title': '小米蓝牙耳机青春版',
					price: '59', heat: '2.7万人评价',reviewDesc: '中国人终于可以不要到国外去买电饭煲了！坐在家里点点手...', reviewAuthor: '姚士祥', reviewStatus: true},
				{link: 'https://www.mi.com/yeelight-ceilinglamp/', imgUrl: './static/imgs/xmqtejp.jpg', 'title': '小米圈铁耳机Pro',
					price: '149', heat: '1.9万人评价',reviewDesc: '可以改变色温，光暗，有一键夜灯，功能强大。本来不懂磁...', reviewAuthor: '冼伟强', reviewStatus: true},
				{ link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmxgp.jpg', 'title': '小米小钢炮蓝牙音箱2 白色',
					price: '129', heat: '热门',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
			],
			headset: [
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmtdsqs.jpg', 'title': '小米头戴式耳机 轻松版',
					price: '199', heat: '1919人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmjlej.jpg', 'title': '小米胶囊耳机',
					price: '69', heat: '3.6万人评价',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmqtp.jpg', 'title': '小米圈铁耳机Pro',
					price: '149', heat: '1.8万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmsslyyx.jpg', 'title': '小米随身蓝牙音箱',
					price: '69', heat: '1.9万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmxgply.jpg', 'title': '小米小钢炮蓝牙音箱2',
					price: '129', heat: '2.7万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmfhz.jpg', 'title': '小米方盒子蓝牙音箱2',
					price: '129', heat: '1305人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
				{link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmyyly.jpg', 'title': 'ROIDMI音乐蓝牙车充',
					price: '99', heat: '1880人评价',reviewDesc: '小目标又实现一小步，大目标是两年内把客服MM都买到我...', reviewAuthor: '我本疯狂', reviewStatus: true},
				{ link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmlyyx.jpg', 'title': '小米蓝牙音箱',
					price: '189', heat: '耳机音箱',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
			],
			power: [
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/yddy5000.jpg', 'title': '移动电源5000mAh',
					price: '49', heat: '10.3万人评价',reviewDesc: '特别好的电脑！硬盘，office2016增强版已安装...', reviewAuthor: '陈武', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/zmiyddy.jpg', 'title': 'ZMI移动电源10000mAh',
					price: '99', heat: '4392人评价',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/yddy10000.jpg', 'title': '小米移动电源10000mAh高配版',
					price: '149', heat: '8205人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmyddy.jpg', 'title': '20000mAh小米移动电源2',
					price: '149', heat: '1.6万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmyddy2h.jpg', 'title': '10000mAh小米移动电源2',
					price: '79', heat: '4.5万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmcxb.jpg', 'title': '小米插线板 5孔位',
					price: '39', heat: '2.7万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/usbctz.jpg', 'title': 'USB Type-C充电套装',
					price: '15', heat: '1人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{ link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmzncxb.jpg', 'title': '小米智能插线板',
					price: '69', heat: '电源',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
			],
			card: [
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/yylycc.jpg', 'title': 'ROIDMI音乐蓝牙车充',
					price: '99', heat: '1880人评价',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmcdq.jpg', 'title': '小米USB充电器（2口）',
					price: '49', heat: '8869人评价',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/ch5.jpg', 'title': '彩虹5号电池（10粒装）',
					price: '9.9', heat: '10.3万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/1f2.jpg', 'title': '睿米一分二点烟器',
					price: '79', heat: '432人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmcdc.jpg', 'title': '小米USB充电器（4口）',
					price: '69', heat: '1.3万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/32gcck.png', 'title': 'SanDisk 32GB存储卡',
					price: '89', oldPrice: '98', discountType: 'discount', discount: '享9.1折', heat: '910人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmczcdq.jpg', 'title': '小米车载充电器',
					price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '4.9万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
				{ link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/16gcck.png', 'title': 'SanDisk 16GB存储卡',
					price: '44.9', heat: '电池存储卡',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
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
		margin-bottom: 8px;
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
