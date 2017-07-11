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
        {name: '保护套', key: 'cover'},
        {name: '贴膜', key: 'pasting'},
        {name: '其他配件', key: 'others'}
      ],
      topSubStatus: 'hotGoods',
      currGoods: [],
      leftGoods: [
        {link: 'http://www.mi.com/mj-smartshoes/', imgUrl: './static/imgs/mjydx.jpg'},
        {link: 'http://item.mi.com/1154400010.html', imgUrl: './static/imgs/fhzly.jpg'}
      ],
      hotGoods: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/hm4xtm.jpg', 'title': '红米4X 标准高透贴膜',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '4035人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
        {link: 'https://item.mi.com/buy/mitv4a-43', imgUrl: './static/imgs/hmn4xtm.jpg', 'title': '红米Note4X 3GB+16GB/32GB，4GB+64GB（蓝色）标准高透贴膜',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '9039人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmzjzpg.jpg', 'title': '小米支架式自拍杆',
          price: '79', oldPrice: '89', discountType: 'discount', discount: '享9折', heat: '2549人评价',reviewDesc: '是买给老婆的生日礼物！我们一家在我的带领下差不多都是...', reviewAuthor: '纷飞泪', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmzhzj.jpg', 'title': '小米指环支架',
          price: '19',heat: '1.5万人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/xmzpg.jpg', 'title': '小米自拍杆（线控版）',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '1.2万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/mjssfs.jpg', 'title': '米家随身风扇',
          price: '19.9', heat: '1.9万人评价',reviewDesc: '中国人终于可以不要到国外去买电饭煲了！坐在家里点点手...', reviewAuthor: '姚士祥', reviewStatus: true},
        {link: 'https://www.mi.com/yeelight-ceilinglamp/', imgUrl: './static/imgs/hm4xbfk.jpg', 'title': '红米4X 天鹅绒质感保护壳',
          price: '29', heat: '1729人评价',reviewDesc: '可以改变色温，光暗，有一键夜灯，功能强大。本来不懂磁...', reviewAuthor: '冼伟强', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xm5sptm.jpg', 'title': '小米5s Plus 标准高透贴膜',
          price: '9.9', heat: '热门',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      cover: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xm6bht.jpg', 'title': '小米6 硅胶保护套',
          price: '49', discountType: 'new', discount: '新品', heat: '2763人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/hm4xgtbht.jpg', 'title': '红米Note 4X 高透软胶保护套 透明',
          price: '19', heat: '4541人评价',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmn2bht.jpg', 'title': '小米Note  2 高透软胶保护套',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '2377人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xm5spbht.jpg', 'title': '小米5s Plus 智能翻盖保护套',
          price: '29', oldPrice: '49', discountType: 'discount', discount: '享6折', heat: '3369人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xm5sbht.jpg', 'title': '小米5s 智能立显点阵式保护套',
          price: '49', oldPrice: '79', discountType: 'discount', discount: '享7折', heat: '3777人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmmaxbht.jpg', 'title': '小米Max 超薄肤感软胶保护套',
          price: '29', heat: '1.2万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/hm4gbhk.jpg', 'title': '红米4高配版 超薄肤感软胶保护套',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '1880人评价',reviewDesc: '小目标又实现一小步，大目标是两年内把客服MM都买到我...', reviewAuthor: '我本疯狂', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/hmn4bht.jpg', 'title': '红米Note4 智能显示保护套',
          price: '39', heat: '保护套',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      pasting: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/hm4xtm.jpg', 'title': '红米4X 标准高透贴膜',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '4035人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmpb2tm.jpg', 'title': '小米平板2 标准高透贴膜',
          price: '29', heat: '1815人评价',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xm5tm.jpg', 'title': '小米手机5 钢化玻璃贴膜',
          price: '29', heat: '4.8万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xm5spgttm.jpg', 'title': '小米5s Plus 标准高透贴膜',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '6268人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xm5spgttm.jpg', 'title': '小米5s 标准高透贴膜',
          price: '19', heat: '7080人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/hm4gtm.jpg', 'title': '红米4高配版 标准高透贴膜',
          price: '9.9', oldPrice: '19', discountType: 'discount', discount: '享6折', heat: '3204人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmmaxtm.jpg', 'title': '小米Max 标准高透贴膜',
          price: '19', heat: '1.3万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/hmptm.jpg', 'title': '红米Pro 标准高透贴膜',
          price: '9.9', heat: '贴膜',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      others: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/ymjxjp.png', 'title': '悦米机械键盘',
          price: '299', heat: '558人评价',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmzhzj.jpg', 'title': '小米指环支架',
          price: '19',heat: '1.5万人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmdyspq.jpg', 'title': '小米USB-C电源适配器（45W）',
          price: '99', heat: '492人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/lytgykq.jpg', 'title': '蓝牙语音体感遥控器',
          price: '99', heat: '3667人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbxsbi.jpg', 'title': '小米便携鼠标',
          price: '99', heat: '8901人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/usbczjq.jpg', 'title': 'USB-C至HDMI多功能转接器',
          price: '149', heat: '1505人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/usbczjt.jpg', 'title': 'USB Type-C 转接头',
          price: '5', heat: '6.8万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xm2h1.jpg', 'title': '小米二合一数据线100cm',
          price: '24.9', heat: '其他配件',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
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
