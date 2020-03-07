<template>
  <div class="detail">
    <product-param phone="AI 4K 全面屏电视
" />
    <div class="container">
      <div class="phoneDetail">
        <div class="swipter-left">
          <swiper :options="swiperOption">
            <swiper-slide v-for="(item,index) in list" :key="index">
              <img v-lazy="item.url" alt="">
            </swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
          </swiper>
        </div>
        <div class="phone-info">
          <h3 class="item-title">AI 4K全面屏电视</h3>
          <p class="item-info">相机全新升级/ 960帧超慢动作/手持超级夜景/全球首款双频GPS /骁龙845处理器/红外人脸解锁/ AI变焦双摄/三星AMOLED屏</p>
          <div class="delivery">
            <p>小米自营</p>
            <p>1799元<span class="price">1999元</span></p>
          </div>
          <div class="address">
            <div class="address-info">
              北京 北京市 朝阳区 安定门街道
            </div>
            <p class="nowGoods">有现货</p>
          </div>
          <h3 class="title-h3">选择版本</h3>
          <div class="item-box">
            <div @click="choose=1" :class="{'active':choose==1}">
              6GB+64GB 全网通
            </div>
            <div @click="choose=2" :class="{'active':choose==2}">4GB+64GB 移动4G</div>
          </div>
          <h3 class="title-h3">选择颜色</h3>
          <div class="item-box">
            <div class="item-color active">
              深空灰
            </div>
          </div>
          <div class="totalbox">
            <div class="totalbox-info">
              <div v-show="choose==2">小米CC9 4GB+64GB 移动4G 深灰色</div>
              <div v-loading="choose==1">6GB+64GB 全网通 深灰色</div>
              <div>1799元</div>
            </div>
            <div class="price">总计：1799元</div>
          </div>
          <div class="btn-huge" @click.stop="addCart">
            加入购物车
          </div>
        </div>
      </div>
    </div>
    <div class="price-info">
      <div class="container">
        <h2 class="price-item">价格说明</h2>
        <div class="desc">
          <img src="../assets/imgs/detail/item-price.jpeg" alt="">
        </div>
      </div>
    </div>
    <test-modal :cancel="cancel" @cancel="cancel = false" @submit="submit" sureText="查看购物车" title='提示'>
      <template v-slot:soltbody>
        <div>
          加入购物车成功!
        </div>
      </template>
    </test-modal>
  </div>
</template>

<script>
import ProductParam from "./../components/ProductParam";
import { swiper, swiperSlide } from "vue-awesome-swiper";
import TestModal from "./../components/TestModal";

export default {
  data() {
    return {
      cancel: false,
      choose: 1,
      swiperOption: {
        autoplay: true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        }
      },
      list: [
        { id: 1, url: require("../assets/imgs/detail/phone-1.jpg") },
        { id: 2, url: require("../assets/imgs/detail/phone-2.jpg") },
        { id: 3, url: require("../assets/imgs/detail/phone-3.jpg") }
      ]
    };
  },
  methods: {
    submit() {
      this.cancel = false;
    },
    addCart() {
      this.cancel = true;
    }
  },
  components: {
    ProductParam,
    swiper,
    swiperSlide,
    TestModal
  }
};
</script>

<style lang="scss">
@import "./../assets/scss/base.scss";
@import "./../assets/scss/mixin.scss";
@import "./../assets/scss/config.scss";
.phoneDetail {
  display: flex;
  .swipter-left {
    width: 642px;
    height: 617px;
    img {
      height: 100%;
      width: 100%;
    }
  }
  .phone-info {
    .item-title {
      font-size: 28px;
      padding-top: 30px;
      padding-bottom: 16px;
      height: 26px;
    }
    .item-info {
      font-size: 14px;
      height: 36px;
    }
    .delivery {
      font-size: 16px;
      color: #ff6700;
      margin-top: 26px;
      margin-bottom: 14px;
      border-bottom: 1px solid #cccccc;
      padding-bottom: 15px;
      .price {
        color: #cccccc;
        display: inline-block;
        margin-left: 10px;
        text-decoration: line-through;
      }
    }
    .address {
      margin-top: 20px;
      width: 584px;
      height: 108px;
      border: 1px solid $colorH;
      background-color: $colorK;
      padding: 30px;
      padding-left: 50px;
      font-size: 14px;
      box-sizing: border-box;
    }
    .address-info {
      position: relative;
      color: #666;
      &:before {
        content: "";
        position: absolute;
        top: 0;
        left: -26px;
        display: inline-block;
        @include bgImg(20px, 20px, "../assets/imgs/detail/icon-loc.png");
      }
    }
    .title-h3 {
      font-size: 18px;
      margin-bottom: 20px;
      margin-top: 20px;
    }
    .nowGoods {
      color: $colorA;
      margin-top: 10px;
    }
    .item-box {
      display: flex;
      justify-content: space-between;
      .item-color {
        &::before {
          content: "";
          display: inline-block;
          width: 20px;
          height: 20px;
          background-color: #666;
          vertical-align: middle;
        }
      }
      div {
        width: 287px;
        height: 50px;
        line-height: 50px;
        text-align: center;
        font-size: 16px;
        border: 1px solid $colorH;

        cursor: pointer;
      }
      .active {
        border: 1px solid $colorA;

        color: $colorA;
      }
    }
    .totalbox {
      height: 108px;
      background: #fafafa;
      padding: 24px 33px 29px 30px;
      font-size: 14px;
      margin-top: 50px;
      margin-bottom: 30px;
      -webkit-box-sizing: border-box;
      box-sizing: border-box;
      .totalbox-info {
        display: flex;
        justify-content: space-between;
      }
      .price {
        font-size: 24px;
        color: $colorA;
        margin-top: 15px;
      }
    }
    .btn-huge {
      width: 300px;
      height: 54px;
      line-height: 54px;
      font-size: 16px;
      background-color: $colorA;
      text-align: center;
      color: #ffffff;
      cursor: pointer;
    }
  }
  margin-bottom: 30px;
}
.price-info {
  background-color: #f3f3f3;
  height: 340px;
  .price-item {
    font-size: 24px;
    color: #333;
    padding-top: 38px;
    margin-bottom: 30px;
  }
}
</style>