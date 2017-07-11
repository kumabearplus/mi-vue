<template>
  <div class="around-container">
    <div class="goods-top clearfix">
      <h3 class="top-title">周边</h3>
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
      topTitle: '周边',
      subs: [
        {name: '热门', key: 'hotGoods'},
        {name: '服装', key: 'dress'},
        {name: '米兔', key: 'rabbit'},
        {name: '生活周边', key: 'around'},
        {name: '箱包', key: 'bags'}
      ],
      topSubStatus: 'hotGoods',
      currGoods: [],
      leftGoods: [
        {link: 'http://www.mi.com/selfiestick-tripod/', imgUrl: './static/imgs/xmzjszpg.jpg'},
        {link: 'http://item.mi.com/1164700015.html', imgUrl: './static/imgs/zshmj.jpg'}
      ],
      hotGoods: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/mjydxzn.jpg', 'title': '米家运动鞋(智能版) 男款',
          price: '229', oldPrice: '249', discountType: 'discount', discount: '享9.2折', heat: '1.2万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
        {link: 'https://item.mi.com/buy/mitv4a-43', imgUrl: './static/imgs/zshyj.jpg', 'title': '最生活浴巾·青春系列',
          price: '79', oldPrice: '99', discountType: 'free', discount: '免邮费', heat: '1730人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/8hrjcd.jpg', 'title': '8H乳胶床垫',
          price: '999', heat: '335人评价',reviewDesc: '是买给老婆的生日礼物！我们一家在我的带领下差不多都是...', reviewAuthor: '纷飞泪', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/90flxx.jpg', 'title': '90分旅行箱 20寸',
          price: '269', oldPrice: '299', discountType: 'free', discount: '免邮费', heat: '2.2万人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/90f24lxx.jpg', 'title': '90分旅行箱 24寸',
          price: '319', oldPrice: '349', discountType: 'free', discount: '免邮费', heat: '2.1万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/hjrjz.jpg', 'title': '8H护颈乳胶枕',
          price: '199', oldPrice: '239', discountType: 'discount', discount: '享9折', heat: '1.1万人评价',reviewDesc: '中国人终于可以不要到国外去买电饭煲了！坐在家里点点手...', reviewAuthor: '姚士祥', reviewStatus: true},
        {link: 'https://www.mi.com/yeelight-ceilinglamp/', imgUrl: './static/imgs/xmjjsjb.jpg', 'title': '小米极简都市双肩包',
          price: '129', oldPrice: '149', discountType: 'discount', discount: '享9折', heat: '2.4万人评价',reviewDesc: '可以改变色温，光暗，有一键夜灯，功能强大。本来不懂磁...', reviewAuthor: '冼伟强', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmzjsszpg.jpg', 'title': '小米支架式自拍杆',
          price: '79', heat: '热门',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      dress: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmtxpkn.png', 'title': '小米短袖T恤 扑克脸',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '864人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxcxys.png', 'title': '小米短袖T恤 程序艺术',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '836人评价',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxcdr.png', 'title': '小米短袖T恤 吃豆人',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '774人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmgndx.jpg', 'title': '小米功能短袖Polo衫 男款',
          price: '99', heat: '1657人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxn.png', 'title': '小米短袖T恤 米兔昆仑游 女款',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '411人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxnk.png', 'title': '小米V领短袖T恤 男款',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '3494人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxkjys.png', 'title': '小米短袖T恤 科技艺术',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '781人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmdxtxn.png', 'title': '小米短袖T恤 米兔昆仑游 男款',
          price: '39', heat: '服装',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      rabbit: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/mtbz.jpg', 'title': '60cm柔软米兔抱枕',
          price: '99', oldPrice: '129', discountType: 'discount', discount: '享8折', heat: '1122人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mtgs.jpg', 'title': '13cm皮质米兔挂饰',
          price: '49', heat: '354人评价',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mthjz.jpg', 'title': '米兔多功能护颈枕',
          price: '49', heat: '3303人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mt.jpg', 'title': '经典款米兔（25cm）',
          price: '49', discountType: 'new', discount: '新品', heat: '154人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmtxpkn.png', 'title': '小米短袖T恤 扑克脸',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '864人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxcxys.png', 'title': '小米短袖T恤 程序艺术',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '836人评价',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtxcdr.png', 'title': '小米短袖T恤 吃豆人',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '774人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmtxnk.png', 'title': '小米V领短袖T恤 男款',
          price: '39', heat: '米兔',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      around: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjzxbbx.jpg', 'title': '米家中性笔专用笔芯',
          price: '6.9', heat: '1.1万人评价',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/hhccjcy.jpg', 'title': '花花草草监测仪',
          price: '49',heat: '6517人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjssd.jpg', 'title': '米家LED随身灯 增强版',
          price: '19.9', heat: '3.6万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjssffs.jpg', 'title': '米家随身风扇',
          price: '99', heat: '1.9万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/bxjg.jpg', 'title': '变形金刚特别版声波',
          price: '159', oldPrice: '169', discountType: 'discount', discount: '享9.5折', heat: '2742人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/jssbd.jpg', 'title': '金属鼠标垫 小号',
          price: '49', heat: '1.2万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmsnh.jpg', 'title': '小米电源线收纳盒',
          price: '39', oldPrice: '49', discountType: 'discount', discount: '享8折', heat: '3669人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/sbdd.jpg', 'title': '鼠标垫加大号',
          price: '19', heat: '生活周边',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      bags: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/90flxx.jpg', 'title': '90分旅行箱 20寸',
          price: '269', oldPrice: '299', discountType: 'free', discount: '免邮费', heat: '2.2万人评价',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/90f24lxx.jpg', 'title': '90分旅行箱 24寸',
          price: '319', oldPrice: '349', discountType: 'free', discount: '免邮费', heat: '2.1万人评价',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/hwlv.jpg', 'title': '90分轻户外旅行洗漱包',
          price: '35', oldPrice: '39', discountType: 'discount', discount: '享9折', heat: '3553人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmnpqb.jpg', 'title': '小米简约头层小牛皮钱包',
          price: '89', oldPrice: '129', discountType: 'discount', discount: '享7折', heat: '3419人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmswsj.jpg', 'title': '小米经典商务双肩包',
          price: '89', oldPrice: '99', discountType: 'discount', discount: '享9折', heat: '1.1万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmdssj.jpg', 'title': '小米极简都市双肩包',
          price: '129', oldPrice: '149', discountType: 'discount', discount: '享9折', heat: '2.4万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmxx.jpg', 'title': '小米多功能都市休闲胸包',
          price: '59', oldPrice: '69', discountType: 'discount', discount: '享9折', heat: '2.9万人评价',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmxysj.jpg', 'title': '小米学院休闲双肩包',
          price: '69', heat: '箱包',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
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
