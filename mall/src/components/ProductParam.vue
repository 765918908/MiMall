<template>
  <div class="productParam" :class="{'flixed':fixed}">
    <div class="container">
      <div class="param-box">
        <h3>{{phone}}</h3>
        <div class="info">
          <a href="javascript:;">概述</a>
          <span>|</span>
          <a href="javascript:;">参数</a>
          <span>|</span>
          <a href="javascript:;">用户评价</a>
          <a v-show="phoneText" href="javascript:;" @click.stop="$emit('buynow')" class="btn">{{phoneText}}</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["phone", "phoneText"],
  data() {
    return {
      fixed: false
    };
  },
  methods: {
    initHeight() {
      let scrollTop =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollTop;
      if (scrollTop > 151) {
        this.fixed = true;
      } else {
        this.fixed = false;
      }
    }
  },
  mounted() {
    window.addEventListener("scroll", this.initHeight);
  }
};
</script>

<style lang="scss">
@import "./../assets/scss/base.scss";
@import "./../assets/scss/mixin.scss";
@import "./../assets/scss/config.scss";
.flixed {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  box-shadow: 0 5px 5px #ccc;
  border-top: 1px solid #cccccc;
  background-color: #ffffff;
  z-index: 20;
}
.productParam {
  .param-box {
    background-color: #ffffff;
    height: 70px;
    line-height: 70px;
    display: flex;
    justify-content: space-between;
    .info {
      a {
        color: #666;
        font-size: 14px;
      }
      span {
        display: inline-block;
        margin-left: 10px;
        margin-right: 10px;
      }
      .btn {
        display: inline-block;
        margin-left: 10px;
        color: #ffffff;
        background-color: $colorA;
        padding: 0 20px;
        height: 35px;
        line-height: 35px;
      }
    }
  }
}
</style>