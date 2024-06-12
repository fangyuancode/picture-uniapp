<template>
  <view class="homeLayout pageBg">
    <!-- 轮播图 -->
    <view class="banner">
      <swiper indicator-dots indicator-color="rgba(255,255,255,0.5)" indicator-active-color="#fff" autoplay circular>
        <swiper-item v-for="item in 3">
          <!-- aspectFill图像填充 -->
          <image src="../../common/images/banner1.jpg" mode="aspectFill"></image>
        </swiper-item>
      </swiper>
    </view>
    <!-- 通知公告上下滑动 -->
    <view class="notice">
      <view class="left">

        <uni-icons type="sound-filled" size="20" color="#28b389"></uni-icons>
        <text> 公告</text>
      </view>
      <view class="center">

        <swiper vertical :autoplay="true" :interval="1500" :duration="300" circular>
          <swiper-item>
            <view class="swiper-item">文字</view>
          </swiper-item>
          <swiper-item>
            <view class="swiper-item">文字内容</view>
          </swiper-item>
        </swiper>
      </view>
      <view class="right">
        <uni-icons type="right" size="16" color="#28b389"></uni-icons>
        <text> </text>
      </view>

    </view>

    <!-- 推荐区域 -->
    <view class="select">
      <common-title>
        <template #name> 每日推荐 </template>
        <template #custom>
          <view class="date">
            <uni-icons type="calendar" size="18" color="#28b389"></uni-icons>
            <view class="text">
              <uni-dateformat :date="Date.now()" format="dd日"></uni-dateformat>
            </view>

          </view>
        </template>

      </common-title>
      <view class="content">
        <!-- srcoll-x 横向滑动 -->
        <scroll-view scroll-x>
          <view class="box" v-for="(item,index) in 8 ">
            <image src="../../common/images/preview_small.webp" mode="aspectFill"></image>
          </view>
        </scroll-view>
      </view>
    </view>
    <!-- 专题精选 -->
    <view class="theme">
      <common-title>
        <template #name> 专题精选 </template>
        <template #custom>
          <navigator url="" class="more">moe+</navigator>
        </template>
      </common-title>
      <view class="content">
        <theme-item v-for="item in 8"></theme-item>
        <theme-item :isMore="true"></theme-item>
      </view>
    </view>

  </view>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.banner {
  width: 750rpx;
  padding: 30rpx 0;

  swiper {
    width: 750rpx;
    height: 340rpx;

    &-item {
      width: 100%;
      height: 100%;
      padding: 0 30rpx;

      image {
        width: 100%;
        height: 100%;
        border-radius: 10px;
      }
    }
  }
}

.notice {
  width: 690rpx;
  height: 80rpx;
  line-height: 80rpx;
  background-color: #f9f9f9;
  margin: 0 auto;
  border-radius: 80rpx;
  display: flex;

  .left {
    width: 140rpx;
    display: flex;
    justify-content: center;
    align-items: center;

    text {
      color: $brand-theme-color;
      font-weight: 600;
      font-size: 28rpx;
    }
  }

  .center {
    flex: 1;

    swiper {
      height: 100%;

      &-item {
        height: 100%;
        font-size: 30rpx;
        color: #666;
        // 用于文字过多隐藏,用...代替
        overflow: hidden;
        white-space: nowrap; //不换行
        text-overflow: ellipsis;
      }
    }
  }

  .right {
    width: 70rpx;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}

.select {
  padding-top: 50rpx;

  .date {
    // color: #28b392;
    color: $brand-theme-color;

    display: flex;
    align-items: center;

    .text {
      margin-left: 5rpx;
    }
  }

  .content {
    width: 720rpx;
    margin-left: 30rpx;

    scroll-view {
      white-space: nowrap;

      .box {
        width: 200rpx;
        height: 430rpx;
        display: inline-block;
        margin-right: 15px;

        image {
          width: 100%;
          height: 100%;
          border-radius: 10rpx;
        }
      }

      // 处理最后一个图像的右边距
      .box:last-child {
        margin-right: 30px;
      }
    }
  }
}

.theme {
  padding: 50rpx 0;

  .more {
    font-size: 32rpx;
    color: #888;
  }

  .content {
    margin-top: 30rpx;
    padding: 0 30rpx;
    // 网格布局
    display: grid;
    gap: 15rpx;
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>