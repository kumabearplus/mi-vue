<template>
  <div class="around-container">
    <div class="goods-top clearfix">
      <h3 class="top-title">智能</h3>
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
      topTitle: '智能',
      subs: [
        {name: '热门', key: 'hotGoods'},
        {name: '出行', key: 'outdoor'},
        {name: '健康', key: 'health'},
        {name: '酷玩', key: 'play'},
        {name: '路由器', key: 'router'}
      ],
      topSubStatus: 'hotGoods',
      currGoods: [],
      leftGoods: [
        {link: 'http://www.mi.com/roomrobot/', imgUrl: './static/imgs/mjsdjqr.jpg'},
        {link: 'http://www.mi.com/dianfanbao2-4l/', imgUrl: './static/imgs/mjdfb4l.jpg'}
      ],
      hotGoods: [
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmtzc.jpg', 'title': '小米体脂秤',
          price: '199', heat: '简约纤薄，隐藏式 LED 显示屏',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: true},
        {link: 'https://item.mi.com/buy/mitv4a-43', imgUrl: './static/imgs/mjxjtc.jpg', 'title': '米家全景相机套装',
          price: '1599', oldPrice: '1699', discountType: 'discount', discount: '享9.5折', heat: '2388万有效像素，IP67级防水防尘',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmphc.png', 'title': '九号平衡车 Plus',
          price: '3499', discountType: 'new', discount: '新品', heat: '35km超长续航，一键自动跟随',reviewDesc: '是买给老婆的生日礼物！我们一家在我的带领下差不多都是...', reviewAuthor: '纷飞泪', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/mjczkqjhq.jpg', 'title': '米家车载空气净化器',
          price: '420', oldPrice: '449', discountType: 'discount', discount: '享9.4折',heat: '双风机循环气流，高效净化车内空气',reviewDesc: '忠实米粉，买了小米手机，配了米粉卡，买了小米电视，又...', reviewAuthor: '在路上', reviewStatus: true},
        {link: 'https://www.mi.com/electric-toothbrush/', imgUrl: './static/imgs/mtjmjqr.jpg', 'title': '米兔积木机器人 履带机甲',
          price: '499', discountType: 'new', discount: '新品', heat: '履带底盘，智能操控，百变拼插',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/mtetdhsb2.jpg', 'title': '米兔儿童电话手表2',
          price: '399', discountType: 'new', discount: '新品', heat: 'AMOLED高清彩屏，6 天超长续航',reviewDesc: '中国人终于可以不要到国外去买电饭煲了！坐在家里点点手...', reviewAuthor: '姚士祥', reviewStatus: true},
        {link: 'https://www.mi.com/yeelight-ceilinglamp/', imgUrl: './static/imgs/xmwrjtc.jpg', 'title': '小米无人机4K版套装',
         price: '2969', oldPrice: '2999', discountType: 'discount', discount: '享9.9折', heat: '探索触手可及的新视角',reviewDesc: '可以改变色温，光暗，有一键夜灯，功能强大。本来不懂磁...', reviewAuthor: '冼伟强', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmvryj.jpg', 'title': '小米VR眼镜',
          price: '299', heat: '热门',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      outdoor: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjxb.jpg', 'title': '米家小白智能摄像机',
          price: '399', heat: '360° 全景拍摄，1080P 高清摄像',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/dzlztzxc.jpg', 'title': '电助力折叠自行车',
          price: '2999', heat: '力矩传感电助力，折叠便携设计',reviewDesc: '超大的，就是厚了一点。运费安装费有点贵。', reviewAuthor: '假の太逼真', reviewStatus: true},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/mjdjj.jpg', 'title': '小米米家对讲机',
          price: '249', heat: '限时特惠，满2件减40元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmphc.jpg', 'title': '九号平衡车',
          price: '1999', heat: '年轻人的酷玩具，骑行遥控两种玩法',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmydsb.jpg', 'title': 'Amazfit 运动手表',
          price: '799', heat: '蓝牙听歌，运动心率，智能通知提醒',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xywd.jpg', 'title': '小蚁微单相机M1双镜头套机',
          price: '2999', heat: '限时特惠，下单立减100元',reviewDesc: '外形大方，超大气，安装师傅细心，打完眼还给打扫干净。...', reviewAuthor: '贤妻良母', reviewStatus: false},
        {link: 'https://item.mi.com/1170900022.html', imgUrl: './static/imgs/xmsh2.jpg', 'title': '小米手环2',
          price: '149', discountType: 'free', discount: '免邮费', heat: 'OLED 显示屏幕，升级计步算法',reviewDesc: '小目标又实现一小步，大目标是两年内把客服MM都买到我...', reviewAuthor: '我本疯狂', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/mjczkqjhqlx.jpg', 'title': '米家车载空气净化器滤芯',
          price: '59', heat: '出行',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      health: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjtd2.jpg', 'title': '米家飞利浦智睿台灯二代',
          price: '199', heat: '感知环境光，主动优化场景照明',reviewDesc: '特别好的电脑！硬盘，office2016增强版已安装...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmctd.jpg', 'title': 'Yeelight床头灯',
          price: '229', oldPrice: '249', discountType: 'discount', discount: '享9.2折', heat: '触摸式操作体验，给卧室1600万种颜色',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmtizc.jpg', 'title': '小米体重秤',
          price: '99', heat: '100克，喝杯水都可感知的精准',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjznsxj.jpg', 'title': '米家智能摄像机 1080P',
          price: '189', oldPrice: '199', discountType: 'discount', discount: '享9.5折', heat: '10米红外夜视范围，双向语音沟通',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjxyj.jpg', 'title': '米家iHealth血压计',
          price: '399', heat: '爸妈上手就会用的智能血压计',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjpmjcy.jpg', 'title': '米家PM2.5检测仪',
          price: '399', heat: '一体黑 OLED 屏，智能联动',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/kqjhqlx.jpg', 'title': '空气净化器滤芯',
          price: '149', heat: '高效净化，可吸入颗粒物、甲醛',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmszjcb.jpg', 'title': '小米水质TDS检测笔',
          price: '39', heat: '健康',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      play: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mtetsb.jpg', 'title': '米兔儿童手表Q',
          price: '249', oldPrice: '299', discountType: 'discount', discount: '享9折', heat: '11重安全设计，五重精准定位',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mtzngsj.jpg', 'title': '米兔智能故事机',
          price: '199', heat: '微信远程互动，智能语音交互',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjznjttz.png', 'title': '米家智能家庭礼品装',
          price: '329', heat: '智能联动，让生活更便捷',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjdgnwg.jpg', 'title': '米家多功能网关',
          price: '149', heat: '米家智能配件控制中心',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/ywbjq.jpg', 'title': '烟雾报警器',
          price: '149', heat: '远程报警，定期自检提醒',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mjzncz.jpg', 'title': '米家智能插座(ZigBee版)',
          price: '69', heat: '实际功率检测，电量统计，定时开关',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmwlsyj.jpg', 'title': '小米网络收音机增强版',
          price: '149', heat: '蓝牙 Wi-Fi 双无线，专业扬声器',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xfznsxj.jpg', 'title': '小方智能摄像机',
          price: '129', heat: '酷玩',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
      ],
      router: [
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmlyq3.jpg', 'title': '小米路由器3',
          price: '149', discountType: 'free', discount: '免邮费', heat: '四天线设计，更快更强',reviewDesc: '电饭煲很精巧，外观高大上，煮饭香又香。客服妹子，我叫...', reviewAuthor: '陈武', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmlyq3c.jpg', 'title': '小米路由器3C',
          price: '99', discountType: 'free', discount: '免邮费', heat: 'APP智能控制，安全防蹭网',reviewDesc: '真的很美！大小完全符合我的标准，厚度轻度都很好！外观...', reviewAuthor: '刘洋', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmwffdq.jpg', 'title': '小米WiFi放大器 2',
          price: '49', heat: '适配主流路由器，两步完成设置',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmlyq.jpg', 'title': '小米路由器 HD',
          price: '1299', heat: '全新金属机身设计，4x4全向性天线',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmwfdlm.jpg', 'title': '小米WiFi电力猫',
          price: '249', heat: '需要与路由器产品搭配使用',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmlyqp.jpg', 'title': '小米路由器 Pro',
          price: '499', heat: '全新金属机身设计，4x4全向性天线',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        {link: 'http://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/xmlyq3g.jpg', 'title': '小米路由器3G',
          price: '249', discountType: 'new', discount: '新品', heat: '双核全千兆设计，USB 3.0',reviewDesc: '什么都有了就差客服妹子来暖床了，妹子你什么时间来啊', reviewAuthor: '小红哥哥', reviewStatus: true},
        { link: 'https://www.mi.com/roomrobot/', imgUrl: './static/imgs/xmwx.jpg', 'title': '小米千兆网线',
          price: '14.9', heat: '路由器',reviewDesc: '', moreUrl: 'https://www.mi.com/buytv/',reviewAuthor: '冼伟强', reviewStatus: false}
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
