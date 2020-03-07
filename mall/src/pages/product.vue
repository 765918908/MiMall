<template>
  <div class="product">
    <product-param phone="小米CC9" phoneText="立即购买" @buynow="buynow" />
    <div class="content">
      <h2>小米CC9</h2>
      <p class="info">3200万自拍，4800万三摄</p>

      <p class="detail"><a href="javascript:;">全球首款双频</a><span>|</span><a href="javascript:;">骁龙845</a><span>|</span><a href="javascript:;">AI 变焦双摄</a><span>|</span><a href="javascript:;">红外人脸识别</a></p>
      <p class="price">¥1799</p>
    </div>
    <div class="item-bg">
      <div class="container">
        <img v-lazy="require('../assets/imgs/product/product-bg-2.png')" alt="">
      </div>
    </div>
    <div class="item-bg2">
    </div>
    <div class="swiper-box">
      <swiper :options="swiperOption">
        <swiper-slide><img src="../assets/imgs/product/gallery-2.png" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/imgs/product/gallery-3.png" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/imgs/product/gallery-4.png" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/imgs/product/gallery-5.jpg" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/imgs/product/gallery-6.jpg" alt=""></swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
    <div class="viewbox">
      <h2>60帧超慢动作摄影</h2>
      <h2>慢慢回味每一瞬间的精彩</h2>
      <div class="mini-text">
        <p>后置960帧电影般超慢动作视频，将眨眼间的美妙展现得淋漓尽致！</p>
        <p>更能AI 精准分析视频内容，15个场景智能匹配背景音效。</p>

      </div>
      <div class="video-bg" @click="showSlide=true"></div>
      <div class="view-over">
        <div class="mask" @click.stop="showSlide=false" v-if="showSlide"></div>
        <div class="video-box" :class="{'slide':showSlide}">
          <span class="close-btn" @click.stop="showSlide=false"></span>
          <video @click.stop src="../assets/imgs/product/video.mp4" muted autoplay controls="controls"></video>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import ProductParam from "./../components/ProductParam";
import { swiper, swiperSlide } from "vue-awesome-swiper";

export default {
  data() {
    return {
      showSlide: false,
      swiperOption: {
        autoplay: true,
        slidesPerView: 3,
        spaceBetween: 30,
        freeMode: true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        }
      }
    };
  },
  methods: {
    openShowSlide() {
      this.showSlide = true;
    },
    closeShowSlide() {
      this.showSlide = false;
    },
    buynow() {
      this.$router.push({
        path: "/detail/13"
      });
    }
  },
  components: {
    ProductParam,
    swiper,
    swiperSlide
  }
};
</script>

<style lang="scss">
@import "./../assets/scss/base.scss";
@import "./../assets/scss/mixin.scss";
@import "./../assets/scss/config.scss";

.content {
  height: 718px;
  width: 100%;
  background: url("../assets/imgs/product/product-bg-1.png") no-repeat center;
  text-align: center;
  h2 {
    font-size: 80px;
    padding-top: 30px;
  }
  .info {
    font-size: 25px;
    font-weight: 1000;
    letter-spacing: 10px;
  }
  .detail {
    margin-top: 20px;
    a {
      display: inline-block;
      font-size: 16px;
      color: #333;
    }
    span {
      display: inline-block;
      margin-left: 10px;
      margin-right: 10px;
    }
  }
  .price {
    font-size: 30px;
    font-weight: 500;
    margin-top: 40px;
  }
}
.item-bg {
  background-color: #ffffff;
  margin: 50px 0px;
  .container {
    img {
      width: 100%;
      height: 100%;
    }
  }
}
.item-bg2 {
  height: 638px;
  background: url("../assets/imgs/product/product-bg-3.png") no-repeat center;
  background-size: cover;
}
.swiper-box {
  margin: 35px 0px;
}
.viewbox {
  height: 933px;
  width: 100%;
  background-color: #070708;
  color: #ffffff;
  text-align: center;
  padding-top: 40px;
  .video-bg {
    width: 1226px;
    height: 540px;
    background: url("../assets/imgs/product/gallery-1.png") no-repeat center;
    margin: 30px auto;
    background-size: contain;
    cursor: pointer;
  }
  h2 {
    font-size: 60px;
  }
  .mini-text {
    margin-top: 47px;
    p {
      font-size: 24px;
    }
  }

  .view-over {
    .mask {
      @include position(fixed);
      background-color: #00000070;
      z-index: 99;
    }

    .video-box {
      height: 536px;
      width: 1000px;
      position: fixed;
      left: 50%;
      top: -50%;
      opacity: 0;
      transform: translate(-50%, -50%);
      z-index: 99;
      transition: all 0.6s;

      &.slide {
        top: 50%;
        opacity: 1;
      }
      video {
        object-fit: cover;
        height: 100%;
        width: 100%;
      }
      .close-btn {
        z-index: 100;
        position: absolute;
        right: 20px;
        top: 5px;
        display: inline-block;
        @include bgImg(20px, 20px, "../assets/imgs/icon-close.png");
        cursor: pointer;
      }
    }
  }
}
</style>