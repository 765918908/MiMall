<template>
  <div class="nav-footer">
    <div class="nav-service">
      <div class="container">
        <ul>
          <li>
            <span class=" service-icon">预约维修服务</span>
          </li>
          <li>
            <span class=" qiday-icon">7天无理由退货</span>
          </li>
          <li>
            <span class="shiwuday-icon">15天免费换货</span>
          </li>
          <li>
            <span class="post-icon">满150元包邮</span>
          </li>
        </ul>
      </div>
    </div>
    <div class="nav-mi">
      <div class="footer-logo">
        <img src="/imgs/logo-footer.png" alt="">
        <p>小米商城</p>
      </div>
      <div class="footer-link">
        <p>河畔一角主页 | Vue全栈课程 | React全家桶课程 | 微信支付专项课程（H5+小程序+Node+Mongo）</p>
        <p class="footer-info">Copyright ©2019 <span>mi.futurefe.com</span> All Rights Reserved.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "./../assets/scss/base.scss";
@import "./../assets/scss/mixin.scss";
@import "./../assets/scss/config.scss";
.nav-footer {
  .nav-service {
    color: #666;
    font-size: 16px;
    .container {
      height: 88px;
      background-color: #ffffff;
      @include flex(0);
      ul {
        width: 100%;
        li {
          display: inline-block;
          width: 24%;
          text-align: center;
          border-right: 1px solid #e5e5e5;
          span {
            position: relative;
            &:before {
              position: absolute;
              left: -25px;
              top: 0px;
              content: " ";
              width: 20px;
              height: 20px;
              display: inline-block;
            }
          }
          .service-icon {
            &:before {
              @include bgImg(20px, 20px, "/imgs/icon-setting.png");
            }
          }
          .qiday-icon {
            &:before {
              @include bgImg(20px, 20px, "/imgs/icon-7day.png");
            }
          }
          .shiwuday-icon {
            &:before {
              @include bgImg(20px, 20px, "/imgs/icon-15day.png");
            }
          }
          .post-icon {
            &:before {
              @include bgImg(20px, 20px, "/imgs/icon-post.png");
            }
          }
        }
      }
    }
  }
  .nav-mi {
    height: 234px;
    border-top: 4px solid #f60;
    background-color: #333;
    color: #999;
    font-size: 16px;
    text-align: center;
    .footer-logo {
      margin-top: 46px;
      margin-bottom: 31px;
      img {
        width: 53px;
        height: 36px;
        margin-bottom: 13px;
      }
    }
    .footer-link {
      p {
        span {
          color: #f60;
        }
      }
      .footer-info {
        margin-top: 20px;
      }
    }
  }
}
</style>