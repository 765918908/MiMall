<template>
  <transition name="slide">

    <div v-show="cancel" class="modal" @click.stop="$emit('cancel')">
      <div class="msak"></div>
      <div @click.stop class="modal-box">
        <div class="header">
          {{title}}
          <span class="close-icon" @click.stop="$emit('cancel')"></span>
        </div>
        <div class="body">
          <slot name="soltbody"></slot>

        </div>
        <div class="footer">
          <a href="javascript:;" @click.stop="$emit('submit')" class="btn">{{sureText}}</a>
        </div>
      </div>
    </div>
  </transition>

</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    close() {
      this.cancel = false;
    }
  },
  props: ["cancel", "title", "sureText"]
};
</script>

<style lang="scss">
@import "./../assets/scss/base.scss";
@import "./../assets/scss/mixin.scss";
@import "./../assets/scss/config.scss";
div.modal {
  z-index: 100;
  @include position(fixed, 0%, 0%);

  .msak {
    @include position(fixed);

    background-color: #000000a1;
  }
  &.slide-enter-active,
  &.slide-leave-active {
    transition: all 0.5s;
  }

  &.slide-enter,
  &.slide-leave-to {
    top: -100%;
  }

  div.modal-box {
    @include position(absolute, 40%, 50%, 500px, auto);

    transform: translate(-50%, -50%);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    div.header {
      font-size: 16px;
      height: 60px;
      line-height: 60px;
      font-weight: bold;
      background-color: #f5f5f5;
      padding-left: 12px;
      position: relative;
      .close-icon {
        @include bgImg(15px, 15px, "/imgs/icon-close.png");
        position: absolute;
        right: 22px;
        top: 22px;
        &:hover {
          -ms-transform: scale(1.5, 1.5); /* IE 9 */
          -webkit-transform: scale(1.5, 1.5); /* Safari */
          transform: scale(1.5, 1.5); /* 标准语法 */
          cursor: pointer;
        }
      }
    }

    div.body {
      font-size: 13px;
      background-color: #ffffff;
      padding: 30px;
    }

    div.footer {
      font-size: 14px;
      background-color: #f5f5f5;
      font-size: 16px;
      height: 60px;
      line-height: 60px;
      text-align: center;
      .btn {
        color: #ffffff;
        display: inline-block;
        background-color: $colorA;
        height: 40px;
        width: 80px;
        padding-left: 15px;
        padding-right: 15px;
        text-align: center;
        line-height: 40px;
      }
    }
  }
}
</style>