<template>
  <div id="top-banner">
    <div class="banner-ct"
      @mouseleave="isLeave()">
      <div class="banner-left">
        <ul class="wrap-left">
          <li class="item"
            @mouseenter="isEnter(item.type)"
            v-for="item in sideItems">
            <span>{{item.content}}</span>
            <span class="iconfont">&gt;</span>
          </li>
        </ul>
      </div>
      <div class="banner-detail"
        v-show="goodsStatus">
        <ul class="detail-wrap">
          <li class="item" v-for="item in currGoods">
            <a class="link" :href="item.link">
              <img :src="item.imgUrl" alt="" />
              <span class="text-name">{{item.name}}</span>
            </a>
            <a class="goods-buy"
              v-show="item.buyStatus"
              :href="item.buyUrl">
                选购
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'topBanner',
  data () {
    return {
      currGoods: [],
      goodsStatus: false,
      sideItems: [
        {type: 'miphone', content: '手机 电话卡'},
        {type: 'mipad', content: '笔记本 平板'},
        {type: 'mibox', content: '电视 盒子'},
        {type: 'mirouter', content: '路由器 智能硬件'},
        {type: 'mipower', content: '移动电源 电池 插线板'},
        {type: 'miear', content: '耳机 音响'},
        {type: 'miprotect', content: '保护套 贴膜'},
        {type: 'mistore', content: '线材 支架 存储卡'},
        {type: 'mibag', content: '箱包 服饰'},
        {type: 'mirabbit', content: '兔米 生活周边'}
      ],
      miphone: [
        {link: 'https://www.mi.com/mi6/', buyUrl: 'https://item.mi.com/product/10000041.html', imgUrl: './static/imgs/xm6.png', name: '小米6', buyStatus: true},
        {link: 'https://www.mi.com/max2/', buyUrl: 'https://item.mi.com/product/10000057.html', imgUrl: './static/imgs/max2.png', name: '小米Max2', buyStatus: true},
        {link: 'https://www.mi.com/mi5c/', buyUrl: 'https://item.mi.com/buyphone/mi5c', imgUrl: './static/imgs/mi5c.png', name: '小米5C', buyStatus: true},
        {link: 'https://www.mi.com/minote2/', buyUrl: 'https://item.mi.com/buyphone/minote2', imgUrl: './static/imgs/xiaomiNOTE2.jpg', name: '小米Note 2', buyStatus: true},
        {link: 'https://www.mi.com/mix/', buyUrl: 'https://item.mi.com/buyphone/mix', imgUrl: './static/imgs/MIX.jpg', name: '小米MIX', buyStatus: true},
        {link: 'https://www.mi.com/mi5s', buyUrl: 'https://item.mi.com/buyphone/mi5s', imgUrl: './static/imgs/xm5s.jpg', name: '小米5s', buyStatus: true},
        {link: 'https://www.mi.com/mi5splus/', buyUrl: 'https://item.mi.com/buyphone/mi5splus', imgUrl: './static/imgs/5splus.jpg', name: '小米5s Plus', buyStatus: true},
        {link: 'https://www.mi.com/redminote4x/', buyUrl: 'https://item.mi.com/buyphone/redminote4x', imgUrl: './static/imgs/hmn4x.jpg', name: '红米Note 4X', buyStatus: true},
        {link: 'https://www.mi.com/redmi4x/', buyUrl: 'https://item.mi.com/buyphone/redmi4x', imgUrl: './static/imgs/hm4x.jpg', name: '红米4X', buyStatus: true},
        {link: 'https://www.mi.com/redmi4/', buyUrl: 'https://item.mi.com/buyphone/redmi4', imgUrl: './static/imgs/hm4.jpg', name: '红米4', buyStatus: true},
        {link: 'https://www.mi.com/redmi4a/', buyUrl: 'https://item.mi.com/product/10000039.html', imgUrl: './static/imgs/hm4a.png', name: '红米4A', buyStatus: true},
        {link: 'https://www.mi.com/compare/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/compare.jpg', name: '对比手机', buyStatus: false},
        {link: 'https://www.mi.com/mimobile/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/mimobile.jpg', name: '小米移动 电话卡', buyStatus: false},
        {link: 'https://www.mi.com/xinpeijian/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/4g+.jpg', name: '移动4G+专区', buyStatus: false}
      ],
      mipad: [
        {link: 'https://www.mi.com/mibookair-12/', buyUrl: 'https://item.mi.com/product/10000032.html', imgUrl: './static/imgs/bijiben12.5.jpg', name: '笔记本12.5英寸', buyStatus: true},
        {link: 'https://www.mi.com/mibookair/', buyUrl: 'https://item.mi.com/product/10000061.html', imgUrl: './static/imgs/bijiben13.3.jpg', name: '笔记本13.3英寸', buyStatus: true},
        {link: 'https://www.mi.com/mipad3/', buyUrl: 'https://item.mi.com/product/10000038.html', imgUrl: './static/imgs/mipad3.png', name: '小米平板3', buyStatus: true},
        {link: 'https://item.mi.com/1170700024.html', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/usbc-dyspq.jpg', name: 'USB-C电源适配器', buyStatus: false},
        {link: 'https://item.mi.com/1163000011.html', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/usbc-zjq.jpg', name: 'USB-C转接器', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=neidanbao', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/neidanbao.jpg', name: '小米笔记本内胆包', buyStatus: false},
        {link: 'https://www.mi.com/keyboard/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/ymjp.jpg', name: '悦米机械键盘', buyStatus: false},
        {link: 'https://www.mi.com/mouse/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/shubiao.jpg', name: '小米便携鼠标', buyStatus: false},
        {link: 'https://www.mi.com/mouse-2/', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/wxsb.png', name: '小米无线鼠标', buyStatus: false},
        {link: 'https://list.mi.com/59', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/xmsbd.jpg', name: '鼠标垫', buyStatus: false},
        {link: 'https://item.mi.com/product/5770.html', buyUrl: '//item.mi.com/buyphone/mi5', imgUrl: './static/imgs/USBC.jpg', name: 'DisplayPort转接器', buyStatus: false}
      ],
      mibox: [
        {link: 'https://www.mi.com/mitv4/49/', imgUrl: './static/imgs/xmds_49.png', name: '小米电视4 49英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4/55/', imgUrl: './static/imgs/xmds_55.png', name: '小米电视4 55英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4/65/', imgUrl: './static/imgs/xmds_65.png', name: '小米电视4 65英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4A/43/', imgUrl: './static/imgs/xmds4a_43.png', name: '小米电视4A 43英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4A/49/', imgUrl: './static/imgs/xmds4a_49.png', name: '小米电视4A 49英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4A/55/', imgUrl: './static/imgs/xmds4a_55.jpg', name: '小米电视4A 55英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv4A/65/', imgUrl: './static/imgs/xmds4a_65.jpg', name: '小米电视4A 65英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv3s/48/', imgUrl: './static/imgs/mitv3s48.jpg', name: '小米电视3s 48英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv3s/55/', imgUrl: './static/imgs/mitv3s55.png', name: '小米电视3s 55英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv3s/60/', imgUrl: './static/imgs/mitv3s60.png', name: '小米电视3s 60英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv3s/65flat/', imgUrl: './static/imgs/mitv3s65.png', name: '小米电视3s 65英寸', buyStatus: false},
        {link: 'https://www.mi.com/mitv3s/65/', imgUrl: './static/imgs/mitv3sqm65.jpg', name: '小米电视3s 65英寸 曲面', buyStatus: false},
        {link: 'https://www.mi.com/mitv3/70/', imgUrl: './static/imgs/mitv3s70.png', name: '小米电视3 70英寸', buyStatus: false},
        {link: 'https://www.mi.com/mibox3s/', imgUrl: './static/imgs/mihezi3s.png', name: '小米盒子3s', buyStatus: false},
        {link: 'https://www.mi.com/mibox3c/', imgUrl: './static/imgs/mihezi3c.png', name: '小米盒子3c', buyStatus: false},
        {link: 'https://www.mi.com/hezi3s/', imgUrl: './static/imgs/hezi3s.jpg', name: '小米盒子3 增强版', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=yinxiang', imgUrl: './static/imgs/jtyx.jpg', name: '家庭音响', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=tv_service', imgUrl: './static/imgs/azfw.png', name: '安装服务', buyStatus: false},
        {link: 'https://list.mi.com/tvboxpj', imgUrl: './static/imgs/dianshipeijian.jpg', name: '电视盒子配件', buyStatus: false}
      ],
      mirouter: [
        {link: 'https://search.mi.com/search_%E5%B9%B3%E8%A1%A1%E8%BD%A6', imgUrl: './static/imgs/phcplus.jpg', name: '九号平衡车', buyStatus: false},
        {link: 'https://list.mi.com/174', imgUrl: './static/imgs/jiqiren.jpg', name: '米家扫地机器人及配件', buyStatus: false},
        {link: 'https://www.mi.com/mivr/', imgUrl: './static/imgs/VRPLAY3.png', name: '小米VR眼镜', buyStatus: false},
        {link: 'https://www.mi.com/miwifi3/', imgUrl: './static/imgs/luyouqi.jpg', name: '小米路由器', buyStatus: false},
        {link: 'https://www.mi.com/mibicycle/', imgUrl: './static/imgs/zxc.jpg', name: '电助力折叠自行车', buyStatus: false},
        {link: 'https://www.mi.com/kettle/', imgUrl: './static/imgs/shuihu.jpg', name: '米家恒温电水壶', buyStatus: false},
        {link: 'https://www.mi.com/carair/', imgUrl: './static/imgs/czjhq.jpg', name: '米家车载空气净化器', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=shoubiao', imgUrl: './static/imgs/dianhuashoubiao.jpg', name: '手表', buyStatus: false},
        {link: 'https://www.mi.com/dianfanbao/', imgUrl: './static/imgs/dianfanbao.jpg', name: '米家智能电饭煲', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=shexiangji', imgUrl: './static/imgs/xiaobai.jpg', name: '智能摄像机/相机/微单', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=jinghuaqilvxin', imgUrl: './static/imgs/jinghuaqilvxin.jpg', name: '净化器及滤芯', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=water', imgUrl: './static/imgs/jingshuiqiandlvxin.jpg', name: '净水器及滤芯', buyStatus: false},
        {link: 'https://list.mi.com/accessories/shouhuan', imgUrl: './static/imgs/shouhuan.jpg', name: '手环及配件', buyStatus: false},
        {link: 'https://search.mi.com/search_%E7%B1%B3%E5%85%94%E7%A7%AF%E6%9C%A8%E6%9C%BA%E5%99%A8%E4%BA%BA', imgUrl: './static/imgs/mijiqiren.jpg', name: '米兔积木机器人及配件', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=smartlamp', imgUrl: './static/imgs/zhinengdeng.jpg', name: '智能灯', buyStatus: false},
        {link: 'https://www.mi.com/mitu/', imgUrl: './static/imgs/gushiji.jpg', name: '米兔智能故事机', buyStatus: false},
        {link: 'https://list.mi.com/130', imgUrl: './static/imgs/zhinengjiatingtaozhuang.jpg', name: '智能家庭组合', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=xueyaji', imgUrl: './static/imgs/xueyaji.jpg', name: '血压计', buyStatus: false},
        {link: 'https://search.mi.com/search_%E7%A7%A4', imgUrl: './static/imgs/tizc.jpg', name: '体重秤 / 体脂秤', buyStatus: false},
        {link: 'https://www.mi.com/scooter2/', imgUrl: './static/imgs/huabanche.jpg', name: '电动滑板车', buyStatus: false},
        {link: 'https://list.mi.com/155', imgUrl: './static/imgs/wurenji.jpg', name: '小米无人机', buyStatus: false},
        {link: 'https://www.mi.com/mj-carcorder/', imgUrl: './static/imgs/jly.jpg', name: '米家行车记录仪', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=duijiangji', imgUrl: './static/imgs/djj.jpg', name: '小米米家对讲机', buyStatus: false},
        {link: 'https://list.mi.com/26?cfrom=search', imgUrl: './static/imgs/znyjdaohang.jpg', name: '全部智能硬件', buyStatus: false}      
      ],
      mipower: [
        {link: 'https://www.mi.com/dianyuan/', imgUrl: './static/imgs/dianyuan.jpg', name: '小米移动电源', buyStatus: false},
        {link: 'https://list.mi.com/125', imgUrl: './static/imgs/cxb.jpg', name: '插线板', buyStatus: false},
        {link: 'https://list.mi.com/13', imgUrl: './static/imgs/pinpaidianyuan.jpg', name: '品牌移动电源', buyStatus: false},
        {link: 'https://list.mi.com/dyfj', imgUrl: './static/imgs/dianyuanfujian.jpg', name: '移动电源附件', buyStatus: false},
        {link: 'https://list.mi.com/15', imgUrl: './static/imgs/chongdianqi.jpg', name: '充电器', buyStatus: false},
        {link: 'https://item.mi.com/1154300033.html', imgUrl: './static/imgs/5Battery2.jpg', name: '彩虹5号电池', buyStatus: false},
        {link: 'https://item.mi.com/1155000010.html', imgUrl: './static/imgs/7Battery2.jpg', name: '彩虹7号电池', buyStatus: false}
      ],
      miear: [
        {link: 'https://www.mi.com/headphone/', imgUrl: './static/imgs/toudai.jpg', name: '小米头戴式耳机', buyStatus: false},
        {link: 'https://www.mi.com/headphone2/', imgUrl: './static/imgs/tdsqs.jpg', name: '头戴式耳机轻松版', buyStatus: false},
        {link: 'https://www.mi.com/earphonetype-c/', imgUrl: './static/imgs/xmjzej.jpg', name: '小米降噪耳机', buyStatus: false},
        {link: 'https://www.mi.com/earphonepro/', imgUrl: './static/imgs/qtpro.jpg', name: '小米圈铁耳机 Pro', buyStatus: false},
        {link: 'https://www.mi.com/quantie/', imgUrl: './static/imgs/quantie.jpg', name: '小米圈铁耳机', buyStatus: false},
        {link: 'https://www.mi.com/capsuleearphone/', imgUrl: './static/imgs/jiaonang.jpg', name: '小米胶囊耳机', buyStatus: false},
        {link: 'https://www.mi.com/huosai3/', imgUrl: './static/imgs/huosai.jpg', name: '小米活塞耳机清新版', buyStatus: false},
        {link: 'https://list.mi.com/accessories/tag?id=lanyaerji', imgUrl: './static/imgs/bluetoothheadset.jpg', name: '小米蓝牙耳机', buyStatus: false},
        {link: 'https://www.mi.com/sportearphone/', imgUrl: './static/imgs/yundong.jpg', name: '小米运动蓝牙耳机', buyStatus: false},
        {link: 'https://list.mi.com/18', imgUrl: './static/imgs/pinpai.jpg', name: '品牌耳机', buyStatus: false},
        {link: 'https://www.mi.com/wifispeaker/', imgUrl: './static/imgs/wlyx.jpg', name: '小米网络音响', buyStatus: false},
        {link: 'https://www.mi.com/pocketaudio/', imgUrl: './static/imgs/pocketaudio.png', name: '小米蓝牙音箱', buyStatus: false},
        {link: 'https://www.mi.com/littleaudio/', imgUrl: './static/imgs/suishen.jpg', name: '小米随身蓝牙音箱', buyStatus: false},
        {link: 'https://www.mi.com/yinxiang/', imgUrl: './static/imgs/xiaogangpao2-hei.jpg', name: '小钢炮音箱 2', buyStatus: false},
        {link: 'https://www.mi.com/bluetooth-speaker/', imgUrl: './static/imgs/fhzlyyx.jpg', name: '小米方盒子蓝牙音箱2', buyStatus: false},
        {link: 'https://item.mi.com/1154400010.html', imgUrl: './static/imgs/fhz.jpg', name: '小米方盒子蓝牙音箱', buyStatus: false},
        {link: 'https://www.mi.com/alarmclock/', imgUrl: './static/imgs/naozhong.jpg', name: '小米音乐闹钟', buyStatus: false},
        {link: 'https://item.mi.com/1163100008.html', imgUrl: './static/imgs/mituyx.jpg', name: '小米米兔音箱', buyStatus: false},
        {link: 'https://item.mi.com/1164900007.html', imgUrl: './static/imgs/chechong.jpg', name: '音乐蓝牙车充', buyStatus: false}
      ],
      miprotect: [
        {link: 'https://list.mi.com/9', imgUrl: './static/imgs/tiemo.jpg', name: '贴膜', buyStatus: false},
        {link: 'https://list.mi.com/8', imgUrl: './static/imgs/baohutao.jpg', name: '保护套/保护壳', buyStatus: false}
      ],
      mistore: [
        {link: 'https://list.mi.com/16', imgUrl: './static/imgs/xiancai.jpg', name: '线材', buyStatus: false},
        {link: 'https://search.mi.com/search_%E8%87%AA%E6%8B%8D%E6%9D%86', imgUrl: './static/imgs/zipaigan.jpg', name: '自拍杆', buyStatus: false},
        {link: 'https://list.mi.com/5', imgUrl: './static/imgs/zhijia.jpg', name: '手机支架', buyStatus: false},
        {link: 'https://list.mi.com/27', imgUrl: './static/imgs/cunchu.jpg', name: '存储卡', buyStatus: false}
      ],
      mibag: [
        {link: 'https://list.mi.com/23', imgUrl: './static/imgs/xiangbao.jpg', name: '箱包', buyStatus: false},
        {link: 'https://search.mi.com/search_%E6%97%85%E8%A1%8C%E7%AE%B1', imgUrl: './static/imgs/lvxingxiang.jpg', name: '90分旅行箱', buyStatus: false},
        {link: 'https://list.mi.com/22', imgUrl: './static/imgs/huise2.jpg', name: '服饰', buyStatus: false},
        {link: 'https://search.mi.com/search_%E8%BF%90%E5%8A%A8%E9%9E%8B', imgUrl: './static/imgs/ydx.jpg', name: '米家运动鞋 智能版', buyStatus: false},
        {link: 'https://www.mi.com/ts-sunglasses/', imgUrl: './static/imgs/tyj.jpg', name: 'TS 尼龙偏光太阳镜', buyStatus: false}
      ],
      mirabbit: [
        {link: 'http://mitu.mi.com/', imgUrl: './static/imgs/mitu.jpg', name: '米兔玩偶', buyStatus: false},
        {link: 'https://list.mi.com/24', imgUrl: './static/imgs/zhoubian1.jpg', name: '生活周边', buyStatus: false},
        {link: 'https://www.mi.com/zazhi/index.html?1021', imgUrl: './static/imgs/zazhi.jpg', name: '《小米》会刊', buyStatus: false},
        {link: 'https://search.mi.com/search_%E6%9C%80%E7%94%9F%E6%B4%BB', imgUrl: './static/imgs/mj.jpg', name: '毛巾/浴巾', buyStatus: false},
        {link: 'https://search.mi.com/search_%E4%B9%B3%E8%83%B6', imgUrl: './static/imgs/rjcd.jpg', name: '8H乳胶床品', buyStatus: false}
      ]

    }
  },
  ready () {
  },
  methods: {
    isEnter (currType) {
      this.currGoods = this[currType]
      this.goodsStatus = true
    },
    isLeave () {
      this.goodsStatus = false
    }
  }
}
</script>

<style scoped lang="scss">
  #top-banner {
    position: relative;
    width: 1226px;
    margin: 0 auto;
    >.banner-ct {
      position: absolute;
      left: 0;
      top: 0;
      width: 235px;
      padding: 20px 0;
      background: rgba(0, 0, 0, 0.3);
      z-index: 10;
      >.banner-left {
        .wrap-left {
          width: 235px;
          height: 420px;
          list-style: none;
          >.item {
            box-sizing: border-box;
            width: 100%;
            height: 42px;
            line-height: 42px;
            font-size: 14px;
            color: #fff;
            display: flex;
            justify-content: space-between;
            padding: 0 30px;
            text-align: center;
            cursor: pointer;
            >.iconfont {
              font-weight: bold;
              font-size: 16px;
            }
            &:hover {
              background: #ff6700;
            }
          }
        }
      }
      >.banner-detail {
        position: absolute;
        left: 235px;
        top: 0;
        z-index: 10;
        border: 1px solid #e0e0e0;
        box-shadow: 3px 8px 16px rgba(0,0,0,0.18);
        .detail-wrap {
          width: 992px;
          height: 460px;
          background: #fff;
          display: flex;
          flex-flow: wrap;
          flex-direction: column;
          align-items: flex-start;
          align-content: flex-start;
          justify-content: flex-start;
          
        }
        .item {
          position: relative;
          display: flex;
          flex-flow: nowrap;
          justify-content: flex-start;
          align-items: center;
          width: 245px;
          height: 76px;
          padding: 0 20px;
          box-sizing: border-box;
          background: #fff;
          cursor: pointer;
          >.link {
            display: flex;
            flex-flow: nowrap;
            justify-content: flex-start;
            align-items: center;
            min-width: 170px;
            >img {
              width: 40px;
              height: 40px;
            }
            >.text-name {
              padding-left: 10px;
              font-size: 14px;
            }
          }
          >.goods-buy {
            position: absolute;
            right: 10px;
            top: 26px;
            width: 58px;
            height: 22px;
            line-height: 22px;
            display: inline-block;
            font-size: 12px;
            text-align: center;
            color: #ff6700;
            border: 1px solid #ff6700;
            &:hover {
              color: #fff;
              background: #ff6700;
            }
          }
        }
      }
    }
  }
</style>
