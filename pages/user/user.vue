<template>
  <view class="userLayout pageBg">
    <view class="userInfo">
      <view class="avatr">
        <image src="../../common/images/avator.jpg" mode="aspectFill"></image>
      </view>
      <view class="ip">100.100.1000.1000</view>
      <view class="address">来自于：宁波</view>
    </view>
    <!-- 个人信息 -->
    <view class="section">
      <view class="list">
        <view class="row" @click="toClassify">
          <view class="left">
            <uni-icons type="download-filled" size="20" color="#28b389"></uni-icons>
            <view class="text">我的下载</view>
          </view>
          <view class="right">
            <view class="text">0</view>
            <uni-icons type="right" size="15"></uni-icons>
          </view>
        </view>

        <view class="row">
          <view class="left">
            <uni-icons type="download-filled" size="20" color="#28b389"></uni-icons>
            <view class="text">我的评分</view>
          </view>
          <view class="right">
            <view class="text">0</view>
            <uni-icons type="right" size="15"></uni-icons>
          </view>
        </view>

        <view class="row">
          <view class="left">
            <uni-icons type="chatboxes-filled" size="20" color="#28b389"></uni-icons>
            <view class="text">联系客服</view>
          </view>
          <view class="right">
            <view class="text">0</view>
            <uni-icons type="right" size="15"></uni-icons>
          </view>
          <!-- 微信小程序时，显示联系客服 -->
          <!-- #ifdef MP-WEIXIN -->
          <button open-type="contact">联系客服</button>
          <!-- #endif -->

          <!-- 其他应用显示拨打电话 -->
          <!-- #ifndef MP -->
          <button @click="clickContact">拨打电话</button>
          <!-- #endif -->

        </view>

      </view>
    </view>

    <view class="section">
      <view class="list">
        <view class="row" v-for="item in 2">

          <view class="left">
            <uni-icons type="download-filled" size="20" color="#28b389"></uni-icons>
            <view class="text">我的下载</view>
          </view>

          <view class="right">
            <view class="text">33</view>
            <uni-icons type="right" size="15"></uni-icons>
          </view>

        </view>
      </view>
    </view>

  </view>
</template>

<script setup>
function toClassify() {
  uni.switchTab({
    url: "/pages/classify/classify",
  });
}
// 点击拨打电话
const clickContact = () => {
  uni.makePhoneCall({
    phoneNumber: "15779666609",
  });
};
</script>

<style lang="scss" scoped>
.userLayout {
  .userInfo {
    display: flex;
    align-items: center;
    flex-direction: column;
    padding: 50rpx 0;

    .avatr {
      height: 160rpx;
      width: 160rpx;
      border-radius: 50%;
      overflow: hidden;

      image {
        width: 100%;
        height: 100%;
      }
    }

    .ip {
      font-size: 44rpx;
      color: #333;
      padding: 20rpx 0 5rpx;
    }

    .address {
      font-size: 28rpx;
      color: #aaa;
    }
  }

  .section {
    width: 690rpx;
    margin: 50rpx auto;
    border: 1px solid #eee;
    border-radius: 10rpx;
    box-shadow: 0 0 30rpx rgnb(0, 0, 0, 0.05);

    .list {
      .row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 30rpx;
        height: 100rpx;
        border-bottom: 1px solid #eee;
        position: relative;
        background-color: #fff;
        &:last-child {
          border-bottom: 0;
        }

        .left {
          display: flex;
          align-items: center;

          .text {
            padding-left: 20rpx;
            color: #666;
          }
        }

        .right {
          display: flex;
          align-items: center;

          .text {
            font-size: 28rpx;
            padding-left: 20rpx;
            color: #aaa;
          }
        }

        button {
          position: absolute;
          top: 0;
          left: 0;
          height: 100rpx;
          width: 100%;
          // 完全透明
          opacity: 0;
        }
      }
    }
  }
}
</style>