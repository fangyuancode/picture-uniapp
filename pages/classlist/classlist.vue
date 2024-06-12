<template>
  <view class="classlist">
    <view class="content">
      <navigator url="" class="item" v-for="iten in 10">
        <!-- aspectFill 以最长边显示 -->
        <image src="../../common/images/preview2.jpg" mode="aspectFill"></image>
      </navigator>
    </view>
  </view>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.classlist {
  .content {
    display: grid;
    grid-template-columns: repeat(3, 1fr); //一行分成三份
    gap: 5rpx; //设置间距
    padding: 5rpx;
    .item {
      height: 440rpx;
      image {
        width: 100%;
        height: 100%;
        display: block;
      }
    }
  }
}
</style>