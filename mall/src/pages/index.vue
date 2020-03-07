<template>
  <div class="index">
    <div class="container">
      <div class="nav-menu">
        <button @click="goScroll"></button>
        <ul>
          <li class="item-menu">
            <a href="javascript:;">手机 电话卡</a>
            <div class="children">
              <ul v-for="(item,index) in menuList" :key="index">
                <li class="children-item" v-for="(arr,j) in item" :key="j">
                  <a href="javascript:;">
                    <img :src="arr.img?arr.img:require('../assets/imgs/item-box-1.png')" alt="">
                    <span>{{arr.name?arr.name:'小米CC9'}}</span>
                  </a>
                </li>
              </ul>
            </div>
          </li>
          <li class="item-menu"><a href="javascript:;">电视 盒子</a></li>
          <li class="item-menu"><a href="javascript:;">笔记本 平板</a></li>
          <li class="item-menu"><a href="javascript:;">家电 插线板</a></li>
          <li class="item-menu"><a href="javascript:;">出行 穿戴</a></li>
          <li class="item-menu"><a href="javascript:;">智能 路由器</a></li>
          <li class="item-menu"><a href="javascript:;">电源 配件</a></li>
          <li class="item-menu"><a href="javascript:;">生活 箱包</a></li>
        </ul>
      </div>
      <div class="swiper-box">
        <swiper :options="swiperOption">
          <!-- slides -->
          <swiper-slide v-for="(item,index) in swiperList" :key="index">
            <a href="javascript:;">
              <img @click="$router.push({path:'/product/13'})" v-lazy="item.img" alt="">
            </a>
          </swiper-slide>
          <!-- Optional controls -->
          <div class="swiper-pagination" slot="pagination"></div>
          <div class="swiper-button-prev" slot="button-prev"></div>
          <div class="swiper-button-next" slot="button-next"></div>
        </swiper>
      </div>
      <div class="ads-box">
        <div class="container">
          <div class="wrapper">
            <a href="javascript:;" v-for="(item,index) in adsList" :key="index">
              <img v-lazy="item.img" alt="">
            </a>
          </div>
        </div>
      </div>
      <div class="banner">
        <a href="javascript:;">
          <img src="../assets/imgs/banner-1.png" alt="">
        </a>
      </div>
    </div>

    <div class="product-box">
      <div class="container">
        <h3>手机</h3>
        <div class="wrapper">
          <div class="banner-left">
            <a href="javascript:;">
              <img src="../assets/imgs/mix-alpha.jpg" alt="">
            </a>
          </div>

          <div class="list-box">
            <div class="list">
              <div class="item" v-for="(i,index) in 4" :key="index">
                <span>新品</span>
                <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6f2493e6c6fe8e2485c407e5d75e3651.jpg" alt="">
                <div class="item-info">
                  <h5>Redmi Note 8 Pro</h5>
                  <p>6400万全场景四摄</p>
                  <p class="price" @click="addCart">1399元</p>
                </div>
              </div>
            </div>
            <div class="list">
              <div class="item" v-for="(i,index) in 4" :key="index">
                <span>新品</span>
                <img src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6f2493e6c6fe8e2485c407e5d75e3651.jpg" alt="">
                <div class="item-info">
                  <h5>Redmi Note 8 Pro</h5>
                  <p>6400万全场景四摄</p>
                  <p class="price" @click="addCart">1399元</p>
                </div>
              </div>
            </div>
          </div>
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
import "swiper/dist/css/swiper.css";
import TestModal from "./../components/TestModal";

import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  data() {
    return {
      showModal: false,
      cancel: false,
      swiperOption: {
        loop: true,
        autoplay: true,
        effect: "cube",
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      },
      swiperList: [
        {
          id: "42",
          img: require("../assets/imgs/slider/slide-1.jpg")
        },
        {
          id: "45",
          img: require("../assets/imgs/slider/slide-2.jpg")
        },
        {
          id: "46",
          img: require("../assets/imgs/slider/slide-3.jpg")
        },
        {
          id: "47",
          img: require("../assets/imgs/slider/slide-4.jpg")
        }
      ],
      menuList: [
        [
          {
            id: 30,
            img: require("@/assets/imgs/item-box-1.png"),
            name: "小米CC9"
          },
          {
            id: 31,
            img: require("../assets/imgs/item-box-2.png"),
            name: "小米8青春版"
          },
          {
            id: 32,
            img: require("../assets/imgs/item-box-2.png"),
            name: "Redmi K20 Pro"
          },
          {
            id: 33,
            img: require("../assets/imgs/item-box-1.png"),
            name: "移动4G专区"
          }
        ],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]
      ],
      adsList: [
        {
          id: 33,
          img: require("@/assets/imgs/ads/ads-1.png")
        },
        {
          id: 48,
          img: require("@/assets/imgs/ads/ads-1.png")
        },
        {
          id: 45,
          img: require("../assets/imgs/ads/ads-3.png")
        },
        {
          id: 47,
          img: require("../assets/imgs/ads/ads-3.png")
        }
      ]
    };
  },
  methods: {
    goScroll() {
      this.$router.push("/#/scroll");
    },
    submit() {
      this.cancel = false;
    },
    addCart() {
      this.cancel = true;
    },
    gogogo() {
      this.cancel = true;
    }
  },
  components: {
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
.swiper-box {
  overflow: hidden;
  .swiper-button-prev {
    left: 274px;
  }
  img {
    height: 100%;
    width: 100%;
  }
}
.nav-menu {
  position: absolute;
  z-index: 10;
  width: 264px;
  height: 460px;
  box-sizing: border-box;
  background-color: rgba(85, 88, 90, 0.48);
  padding: 26px 0;
  font-size: 16px;
  ul {
    .item-menu {
      // position: relative;
      & > a {
        color: #ffffff;
        width: 100%;
        height: 50px;
        line-height: 50px;
        display: inline-block;
        position: relative;
        &:after {
          position: absolute;
          right: 35px;
          top: 17px;
          content: "";
          width: 10px;
          height: 15px;
          display: inline-block;
          @include bgImg(10px, 15px, "../assets/imgs/icon-arrow.png");
        }
      }
      height: 50px;
      line-height: 50px;
      padding-left: 30px;
      &:hover {
        background-color: $colorA;
        .children {
          display: inline-block;
        }
      }
      .children {
        display: none;
        width: 964px;
        height: 458px;
        background-color: #ffffff;
        border: 1px solid #e5e5e5;
        position: absolute;
        left: 264px;
        top: 0px;
        ul {
          display: flex;
          li {
            flex: 1;
            text-align: center;
            height: 75px;
            line-height: 75px;
            padding-left: 50px;
            box-sizing: border-box;
            a {
              display: flex;

              align-items: center;
              img {
                width: 42px;
                height: 35px;
              }
              span {
                color: #000;
                font-size: 12px;
              }
            }
          }
        }
      }
    }
  }
}
.ads-box {
  margin-top: 14px;
  margin-bottom: 31px;
  .container {
    .wrapper {
      display: flex;
      justify-content: space-between;
      a {
        width: 298px;
        height: 167px;
        display: inline-block;

        img {
          width: 100%;
          height: 100%;
        }
      }
    }
  }
}
.banner {
  margin-bottom: 50px;
  a {
    img {
      height: 130px;
      width: 100%;
    }
  }
}
.product-box {
  background-color: #f5f5f5;
  padding: 30px 0 50px;
  .container {
    h3 {
      height: 30px;
      font-size: 20px;
      margin-bottom: 20px;
    }
    .wrapper {
      display: flex;
      .banner-left {
        margin-right: 16px;
        a {
          img {
            height: 619px;
            width: 224px;
          }
        }
      }

      .list-box {
        .list {
          width: 986px;
          margin-bottom: 14px;
          display: flex;
          justify-content: space-between;
          .item {
            width: 236px;
            height: 302px;
            background-color: #fff;
            text-align: center;
            span {
              display: inline-block;
              width: 67px;
              height: 24px;
              font-size: 14px;
              line-height: 24px;
              color: #fff;
              background-color: #7ecf68;
            }
            img {
              height: 195px;
              width: 100%;
            }

            .item-info {
              h5 {
                font-size: 16px;
              }
              p {
                color: #999;
                line-height: 13px;
                margin: 6px auto 13px;
              }
              .price {
                color: #f20a0a;
                font-size: 14px;
                font-weight: 700;
                cursor: pointer;
                &::after {
                  content: " ";
                  @include bgImg(
                    22px,
                    22px,
                    "../assets/imgs/icon-cart-hover.png"
                  );
                  vertical-align: middle;
                  margin-left: 5px;
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>