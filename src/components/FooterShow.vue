<template>
  <footer>
    <div class="service">
      <a :href="item.link" v-for="(item,index) in service" :key="index">
        <span class="iconfont">{{item.icon}}</span>
        <span class="text">{{item.text}}</span>
      </a>
    </div>
    <div class="link">
      <div class="item" v-for="(item,index) in link" :key="index">
        <span class="title">{{item.title}}</span>
        <a :href="key.link" v-for="(key,index) in item.text" :key="key">
          <span>{{key.title}}</span>
        </a>
      </div>
      <div class="contact">
        <span class="phone">小米客服</span>
        <span class="text">7x24小时全天陪伴<br>为您解决问题</span>
        <span class="customer">立即开始咨询</span>
      </div>
    </div>
    <div class="info">
      <div class="info-container">
        <div class="mi-logo"><img src="../assets/logo-footer.png"></div>
        <div class="text">
          <ul>
            <li v-for ="item in content">
              <a :href="item.url">{{item.name}}</a>
              <span class="separate">|</span>
            </li>
          </ul>
          <p>©mi.com 京ICP证110507号 京ICP备10046444号 京公网安备11010802020134号 京网文[2014]0059-0009号 </p>
          <p>违法和不良信息举报电话：185-0130-1238，本网站所列数据，除特殊说明，所有数据均出自我司实验室测试</p>
        </div>
        <div class="info-logo" v-for="item in logo">
          <a :href="item.link">
            <img :src="item.imgUrl">
          </a>
        </div>
      </div>
    </div>
    <div class="slogan"><img src="../assets/slogan2016.png"></div>
  </footer>
</template>

<script>
export default {
  data(){
    return {
      service: [
        {text: '预约维修服务', icon: '\ue609', link: 'https://www.mi.com/static/fast/'},
        {text: '7天无理由退货', icon: '\ue64c', link: 'https://www.mi.com/service/exchange#back'},
        {text: '15天免费换货', icon: '\ue608', link: 'https://www.mi.com/service/exchange#free'},
        {text: '满150元包邮', icon: '\ue604', link: 'https://www.mi.com/service/exchange#mail'},
        {text: '520余家售后网点', icon: '\ue607', link: 'https://www.mi.com/static/maintainlocation/'}
      ],
      link: [
        {
          title: '帮助中心', 
          text: [
            {title: '账户管理', link: 'https://www.mi.com/service/account/register/'},
            {title: '购物指南', link: 'https://www.mi.com/service/buy/buytime/'},
            {title: '订单操作', link: 'https://www.mi.com/service/order/sendprogress/'}
          ]
        },
        {
          title: '服务支持', 
          text: [
            {title: '售后政策', link: 'https://www.mi.com/service/exchange'},
            {title: '自助服务', link: 'http://fuwu.mi.com/'},
            {title: '相关下载', link: 'http://xiazai.mi.com/'}
          ]
        },
        {
          title: '线下门店', 
          text: [
            {title: '小米之家', link: 'https://www.mi.com/c/xiaomizhijia/'},
            {title: '服务网点', link: 'https://www.mi.com/static/maintainlocation/'},
            {title: '零售网点', link: 'https://www.mi.com/static/familyLocation/'}
          ]
        },
        {
          title: '关于小米', 
          text: [
            {title: '了解小米', link: 'https://www.mi.com/about/'},
            {title: '加入小米', link: 'http://hr.xiaomi.com/'},
            {title: '联系我们', link: 'https://www.mi.com/about/contact/'}
          ]
        },
        {
          title: '关注我们', 
          text: [
            {title: '新浪微博', link: 'http://weibo.com/xiaomishangcheng'},
            {title: '小米部落', link: 'http://xiaoqu.qq.com/mobile/share/index.html?url=http%3A%2F%2Fxiaoqu.qq.com%2Fmobile%2Fbarindex.html%3Fwebview%3D1%26type%3D%26source%3Dindex%26_lv%3D25741%26sid%3D%26_wv%3D5123%26_bid%3D128%26%23bid%3D10525%26from%3Dwechat'},
            {title: '官方微信', link: 'https://www.mi.com/index.html#J_modalWeixin'}
          ]
        },
        {
          title: '特色服务', 
          text: [
            {title: 'F 码通道', link: 'https://order.mi.com/queue/f2code'},
            {title: '礼物码', link: 'https://www.mi.com/giftcode/'},
            {title: '防伪查询', link: 'https://order.mi.com/misc/checkitem'}
          ]
        }
      ],
      content: [
        {name:'小米商城',url:'https://www.mi.com/index.html'},
        {name:'MIUI',url:'http://www.miui.com/'},
        {name:'米聊',url:'http://www.miliao.com/'},
        {name:'多看阅读',url:'http://www.duokan.com/'},
        {name:'小米路由器',url:'http://www.miwifi.com/'},
        {name:'视频电话',url:'http://call.mi.com/'},
        {name:'小米天猫店',url:'http://xiaomi.tmall.com/'},
        {name:'小米淘宝直营店',url:'http://shop115048570.taobao.com/'},
        {name:'小米网盟',url:'http://union.mi.com/'},
        {name:'小米移动',url:'https://www.mi.com/mimobile/'},
        {name:'隐私政策',url:'http://www.miui.com/res/doc/privacy/cn.html'},
        {name:'Select Region',url:'https://www.mi.com/#J_modal-globalSites'}
      ],
      logo: [
        {link:'https://privacy.truste.com/privacy-seal/validation?rid=4fc28a8c-6822-4980-9c4b-9fdc69b94eb8&lang=zh-cn',imgUrl:'./static/imgs/truste.png'},
        {link:'https://search.szfw.org/cert/l/CX20120926001783002010',imgUrl:'./static/imgs/cxwz.png'},
        {link:'https://ss.knet.cn/verifyseal.dll?sn=e12033011010015771301369&ct=df&pa=461082',imgUrl:'./static/imgs/kxwz.png'},
        {link:'http://www.315online.com.cn/member/315140007.html',imgUrl:'./static/imgs/wsjy.png'}
      ]
    }
  }
}
</script>

<style lang="scss" scoped>

.iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
}
footer{
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  justify-content: space-between;
  align-content: center;
  .service{
    width: 1226px;
    padding: 30px 0;
    margin: 0 auto 30px;
    border-bottom: 1px solid #e0e0e0;
    background: #fff;
    display: flex;
    justify-content: center;
    >a{
      width: 240px;
      height: 25px;
      border-left: 1px solid #e0e0e0;
      font-size: 16px;
      line-height: 25px;
      color: #616161;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: all .2s;
      &:hover{
        color: #ff6700;
      }
      &:nth-child(1){
        border: none;
      }
      .iconfont{
        font-size: 24px;
        margin-right: 5px;
      }
    }
  }
  .link{
    width: 1226px;
    margin: 0 auto;
    margin-bottom: 30px;
    display: flex;
    justify-content: space-between;
    .item{
      width: 160px;
      height: 112px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      >.title{
        margin: 0 0 26px;
        font-size: 14px;
        color: #424242;
      }
      >a{
        display: flex;
        align-items: center;
        transition: all .2s;
        >span {
          font-size: 12px;
          color: #757575;
          &:hover{
            color: #ff6700;
          }
        }
        
      }
    }
    .contact{
      width: 251px;
      height: 112px;
      border-left: 1px solid #e0e0e0;
      text-align: center;
      color: #616161;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      .phone{
        margin: 0 0 5px;
        font-size: 22px;
        color: #ff6700;
      }
      .text{
        line-height: 16px;
        margin: 0 0 16px;
        font-size: 12px;
      }
      .customer{
        background: #fff;
        color: #ff6700;
        font-size: 12px;
        width: 118px;
        height: 28px;
        line-height: 28px;
        border: 1px solid #ff6700;
        cursor: pointer;
        transition: all .2s;
        &:hover{
          background: #ff6700;
          color: #fff;
        }
      }
    }
  }
  .info{
    width: 100%;
    padding: 30px 0;
    font-size: 12px;
    background: #fafafa;
    .info-container{
      width: 1226px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      .mi-logo>img{
        width: 57px;
        height: 57px;
        margin-right: 10px;
      }
      .text{
        color: #b0b0b0;
        text-align: left;
        margin-right: auto;
        ul {
          display: flex;
          >li:last-child .separate {
            display: none;
          }
          >li {
            font-size: 0;
            >a {
              font-size: 12px;
              color: #757575;
              &:hover {
                color: #ff6700;
              }
            }
            >.separate {
              margin: 0 0.4em;
              font-size: 12px;
              color: #b0b0b0;
            }
          }
        }
        >p:nth-child(1){
          color: #757575;
        }
      }
      .info-logo{
        img {
          width: auto;
          height: 28px;
          margin-left: 7px;
        }
      }
    }
  }
  .slogan{
    text-align: center;
    background: #fafafa;
    padding-bottom: 30px;
  }
}
</style>