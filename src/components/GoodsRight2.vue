<template>
  <div class="goods-right">
    <ul class="goods-right-content">
      <template
        v-for="(goods,index) in currGoods"
        v-if="index < currGoods.length - 1">
        <li class="goods-right-item">
          <span class="discount-label"
            :class="goods.discountType">{{goods.discount}}</span>
          <a :href="goods.link" target="_blank">
            <img :src="goods.imgUrl" alt="" />
          </a>
          <h3 class="goods-title">{{goods.title}}</h3>
          <p class="goods-price">
            {{goods.price}}元
            <span
              v-if="goods.discountType === 'discount'"
              class="old-price">
              {{goods.oldPrice}}元
            </span>
          </p>
          <p class="goods-heat">
            {{goods.heat}}
          </p>
          <div
            v-show="goods.reviewStatus"
            class="review">
            <span class="review-content">{{goods.reviewDesc}}</span>
            <span class="review-author">来自于 {{goods.reviewAuthor}} 的评价</span>
          </div>
        </li>
      </template>
      <ul class="goods-right-small">
        <template v-if="lastGoods">
          <li class="item-small">
            <a :href="lastGoods.link" target="_blank">
              <div class="desc">
                <h3 class="title">
                  {{lastGoods.title}}
                </h3>
                <span class="price">
                  {{lastGoods.price}}元
                </span>
              </div>
              <img class="small-img"
                :src="lastGoods.imgUrl" alt="" />
            </a>
          </li>
          <li class="item-small read-more">
            <a :href="lastGoods.moreUrl" target="_blank">
              <div class="desc">
                <h3 class="title">
                  浏览更多
                </h3>
                <span class="price hot">
                  {{lastGoods.heat}}
                </span>
              </div>
              <span class="iconfont">&#xe620;</span>
              <!-- <img class="small-img" src="../assets/you.png"> -->
            </a>  
          </li>
      </template>
      </ul>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    currGoods: {
      required: true,
      type: Array
    }
  },
  computed: {
    lastGoods: function () {
      if (this.currGoods && this.currGoods.length > 0) {
        return this.currGoods[this.currGoods.length - 1]
      } else {
        return null
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .goods-right {
    float: left;
    width: 992px;
    height: 628px;
    .goods-right-content {
      display: flex;
      flex-flow: row wrap;
      justify-content: flex-start;
      width: 100%;
      height: 100%;
      .goods-right-item {
        position: relative;
        z-index: 1;
        float: left;
        width: 234px;
        height: 246px;
        padding: 34px 0 20px;
        margin-left: 14px;
        margin-bottom: 14px;
        background: #fff;
        transition: all .2s linear;
        &:hover {
          transform: translateY(-1px);
          box-shadow: 5px 5px 20px #ccc;
          .review {
            height: 76px;
            opacity: 1;
          }
        }
        .discount-label {
          position: absolute;
          top: 0;
          left: 50%;
          width: 64px;
          height: 20px;
          line-height: 20px;
          margin-left: -32px;
          font-size: 12px;
          text-align: center;
          color: #fff;
          z-index: 4;
          &.free {
            background-color: #ffac13;
          }
          &.new {
            background-color: #83c44e;
          }
          &.discount {
            background-color: #e53935;
          }
        }
        >a {
          display: block;
          width: 150px;
          height: 150px;
          margin: 0 auto 18px;
          >img {          
            width: 150px;
            height: 150px;
            margin: 0 auto;
          }
        }
        .goods-title {
          margin: 0 10px;
          font-size: 14px;
          font-weight: 400;
          text-align: center;
        }
        .goods-heat {
          height: 18px;
          font-size: 12px;
          text-align: center;
          text-overflow: ellipsis;
          white-space: nowrap;
          overflow: hidden;
          _zoom: 1;
          color: #b0b0b0;
        }
        .old-price {
          color: #b0b0b0;
          text-decoration: line-through;
        }
        .goods-price {
          margin: 0 10px 10px;
          color: #ff6700;
          font-size: 14px;
          text-align: center;
        }
        .review {
          position: absolute;
          left: 0;
          bottom: 0;
          width: 234px;
          font-size: 12px;
          height: 0;
          line-height: 18px;
          overflow: hidden;
          box-sizing: border-box;
          color: #fff;
          background: #ff6700;
          opacity: 0;
          transition: all 0.3s;
          .review-content {
            display: block;
            text-align: left;
            margin: 8px 30px;
          }
          .review-author {
            display: block;
            text-align: center;
            margin-bottom: 8px;
            color: rgba(255,255,255,0.6);
          }
        }   
      }
      .goods-right-small {
        width: 234px;
        height: 260px;
        .item-small {
          width: 234px;
          height: 143px;
          margin: 0 0 14px 14px;
          padding: 30px 0 0 30px;
          background: #fff;
          cursor: pointer;
          transition: all 0.3s;
          box-sizing: border-box;
          &:hover {
            transform: translateY(-1px);
            box-shadow: 5px 5px 20px #ccc;
          }
          &.read-more {
            a {
              .desc {
                .title {
                  font-size: 18px;
                }
              }
            }
          }
          a {padding-top: 10px;
            display: flex;
            .desc {
              width: 91px;
              height: 100%;
              margin-right: 20px;
              .title {
                font-size: 14px;
                text-align: left;
                color: #333;
                font-weight: normal;
                text-overflow: ellipsis;
                white-space: nowrap;
                overflow: hidden;
              }
              .price {
                display: block;
                width: 100%;
                color: #ff6700;
                font-size: 14px;
                text-align: left;
                &.hot {
                  font-size: 12px;
                  color: #757575;
                }
              }
            }
            .iconfont {
              font-family:"iconfont" !important;
              font-style:normal;
              -webkit-font-smoothing: antialiased;
              -moz-osx-font-smoothing: grayscale;
              display: block;
              font-size: 56px;
              line-height: 56px;
              color: #ff6700;
              margin-left: 10px;
            }
            .small-img {
              display: block;
              width: 80px;
              height: 80px;
              margin-right: 20px;
            }
          }
        }
      }
    }
  }

</style>
