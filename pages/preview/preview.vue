<template>
  <view class="preview">
    <swiper circular>
      <swiper-item v-for="iten in 5">
        <image @click="maskChange" src="../../common/images/preview1.jpg" mode="aspectFill"></image>
      </swiper-item>
    </swiper>
    <!-- 图片的遮罩层 -->
    <view class="mask" v-if="maskState">
      <view class="goBack"></view>
      <view class="Count">3 / 9</view>
      <view class="time">
        <uni-dateformat :date="new Date()" format="hh:mm"></uni-dateformat>
      </view>
      <view class="date">
        <uni-dateformat :date="new Date()" format="MM月dd日"></uni-dateformat>

      </view>
      <view class="footer">
        <view class="box">
          <uni-icons type="info" size="28"></uni-icons>
          <view class="text">信息</view>
        </view>
        <view class="box">
          <uni-icons type="star" size="28"></uni-icons>
          <view class="text">5分</view>
        </view>
        <view class="box">
          <uni-icons type="download" size="24"></uni-icons>
          <view class="text">下载</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup>
import { ref } from "vue";
const maskState = ref(true);
const maskChange = () => {
  maskState.value = !maskState.value;
};
</script>

<style lang="scss" scoped>
.preview {
  width: 100%;
  height: 100vh;
  position: relative;
  swiper {
    height: 100%;
    width: 100%;
    image {
      height: 100%;
      width: 100%;
    }
  }
  .mask {
    // 表示父级紧邻的view
    & > view {
      color: #fff;
      position: absolute;
      left: 0;
      right: 0;
      margin: auto;
      width: fit-content; //有多少内容，宽度扩多大
    }
    .goBack {
    }
    .Count {
      top: 10vh;
      background: rgba(0, 0, 0, 0.3);
      font-size: 28rpx;
      border-radius: 40rpx;
      padding: 8rpx 28rpx;
      backdrop-filter: blur(10rpx);
    }
    .time {
      font-size: 140rpx;
      top: calc(10vh + 80rpx);
      font-weight: 100;
      line-height: 1em;
      text-shadow: 0 4rpx rgba(0, 0, 0, 0.3);
    }
    .date {
      font-size: 34rpx;
      top: calc(10vh + 230rpx);

      text-shadow: 0 4rpx rgba(0, 0, 0, 0.3);
    }
    .footer {
      background: rgba(255, 255, 255, 0.8);
      bottom: 10vh;
      width: 65vw;
      height: 120rpx;
      border-radius: 120rpx;
      color: #000;
      display: flex;
      justify-content: space-around;
      align-items: center;
      box-shadow: 0 2rpx 0 rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(10rpx);
      .box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 2rpx 12rpx;
        .text {
          font-size: 26rpx;
          color: $text-font-color-2;
        }
      }
    }
  }
}
</style>