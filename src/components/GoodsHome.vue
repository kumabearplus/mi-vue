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
          price: '1699', heat: '热门',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      tv: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmds3s-55.jpg', 'title': '小米电视3s 55英寸',
          price: '3599', oldPrice: '3999', discountType: 'discount', discount: '享九折', heat: '7月11日-7月14日立减400元',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmds4a-65.png', 'title': '电视4A 65英寸标准版',
          price: '4699', oldPrice: '5699', discountType: 'discount', discount: '享九折', heat: '7月11日-7月14日立减1000元',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmds4a-49.png', 'title': '电视4A 49英寸 人工智能语音版',
          price: '2899', heat: '7月12日-7月14日立减400元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmds4a-55.png', 'title': '电视4A 55英寸 人工智能语音版',
          price: '3599', heat: '7月12日-7月14日立减400元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmds4a-65.png', 'title': '电视4A 65英寸 人工智能语音版',
          price: '6199', heat: '7月12日-7月14日立减1000元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmds4a-55.png', 'title': '电视4A 55英寸标准版',
          price: '3199', heat: '7月12日-7月14日直降400元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmhz3s.jpg', 'title': '小米盒子3s',
          price: '299', heat: '4K超高清机顶盒，64 位处理器',reviewDesc: '小目标又实现一小步，大目标是两年内把客服MM都买到我...', reviewAuthor: '我本疯狂', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/hz3.jpg', 'title': '盒子3 增强版',
          price: '399', heat: '电视影音',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      computer: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbijb13.3.jpg', 'title': '小米笔记本Air13.3英寸',
          price: '5499', heat: '第7代CPU 2G独显 指纹解锁',reviewDesc: '特别好的电脑！硬盘，office2016增强版已安装...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbjb12.5.jpg', 'title': '小米笔记本Air 12.5英寸',
          price: '4999', discountType: 'new', discount: '新品', heat: '集成显卡，酷睿 i5处理器',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbjb12.5.jpg', 'title': '小米笔记本Air 12.5英寸',
          price: '3999', heat: '更轻更薄，像杂志一样随身携带',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbjbbao.jpg', 'title': '小米笔记本内胆包12.5英寸',
          price: '99', heat: '至简纤薄 轻松随行无压力',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmwxsb.png', 'title': '小米无线鼠标',
          price: '69', heat: '耐脏亲肤涂层，人体工学设计',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmbxsb.jpg', 'title': '小米便携鼠标',
          price: '99', heat: '轻薄便携，铝合金外壳 +ABS 材质',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmymjp.png', 'title': '悦米机械键盘',
          price: '279', oldPrice: '289', discountType: 'discount', discount: '享9.7折', heat: '铝合金机身，TTC红轴，87 键',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/usbc-zjq.jpg', 'title': 'USB-C至HDMI多功能转接器',
          price: '149', heat: '电脑',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      home: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjdfb.jpg', 'title': '米家IH电饭煲 3L',
          price: '399', heat: 'IH 电磁环绕加热，3000+ 煮米方案',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/ddys.jpg', 'title': '米家声波电动牙刷',
          price: '199', discountType: 'new', discount: '新品', heat: '磁悬浮声波马达，定制多种刷牙模式',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmjsq.jpg', 'title': '小米净水器（厨下式）',
          price: '1999', heat: 'RO反渗透直出纯净水，隐藏安装',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjkqjhq.png', 'title': '米家空气净化器Pro',
          price: '1499', heat: 'OLED显示屏幕，激光颗粒物传感器',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjdsh.jpg', 'title': '米家恒温电水壶',
          price: '199', heat: '水温智能控制，304 不锈钢内胆',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjqbd.jpg', 'title': '飞利浦智睿球泡灯',
          price: '49', discountType: 'new', discount: '新品', heat: '自由调节亮度，Wi-Fi随时操控',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjtd.jpg', 'title': '米家 LED 智能台灯',
          price: '169', heat: '无可视频闪，四种场景优化调光',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/mjxdd.png', 'title': 'Yeelight LED 吸顶灯',
          price: '379', heat: '家居',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
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
