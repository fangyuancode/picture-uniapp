<template>
  <view class="themeItem">
    <navigator url="/pages/classlist/classlist" class="box" v-if="!isMore">
      <image class="pic" src="../../common/images/classify1.jpg" mode="aspectFill"></image>
      <!-- 遮罩层 -->
      <view class="mask">明星美女</view>
      <view class="tab">3天前更新</view>
    </navigator>

    <!-- 更多 -->
    <!-- 跳转到tabbar页面时需要改变类型 -->
    <navigator url="/pages/classify/classify" open-type="reLaunch" class="box more" v-if="isMore">
      <image class="pic" src="../../common/images/more.jpg" mode="aspectFill"></image>
      <!-- 遮罩层 -->
      <view class="mask">
        <uni-icons type="more-filled" size="34" color="#fff"></uni-icons>
        <view class="text">更多</view>
      </view>
    </navigator>
  </view>
</template>

<script setup>
defineProps({
  isMore: {
    type: Boolean,
    default: false,
  },
});
</script>

<style lang="scss">
.themeItem {
  .box {
    height: 340rpx;
    border-radius: 10rpx;
    // 有图像时，必须加overflow
    overflow: hidden;
    // 父级添加相对定位
    position: relative;
    .pic {
      width: 100%;
      height: 100%;
    }
    .mask {
      width: 100%;
      height: 70rpx;
      // 遮罩层子元素添加绝对定位
      position: absolute;
      bottom: 0;
      left: 0;
      background: rgba(0, 0, 0, 0.2);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      // 将半透明的背景进行模糊，磨砂玻璃效果
      backdrop-filter: blur(20rpx);
      font-weight: 600;
      font-size: 30rpx;
    }
    .tab {
      // 左上角定位
      position: absolute;
      top: 0;
      left: 0;
      background: rgba(250, 129, 90, 0.7);
      backdrop-filter: blur(20rpx);
      color: #fff;
      font-size: 22rpx;
      padding: 6rpx 14rpx;
      // 设置右下的圆角
      border-radius: 0 0 20rpx 0;
      // 进行缩小
      transform: scale(0.8);
      // 偏移位置,以左上角为基准
      transform-origin: left top;
    }
  }
  .box.more {
    .mask {
      width: 100%;
      height: 100%;
      flex-direction: column;
    }
    .text {
      font-size: 28rpx;
    }
  }
}
</style>