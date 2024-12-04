<template>
    <view class="my-container">
      <text class="title">我的信息</text>
      <text>用户名: {{ username }}</text>
      <button @click="navigateToSettings">设置</button>
    </view>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '用户123'
      };
    },
    methods: {
      navigateToSettings() {
        uni.navigateTo({ url: '/pages/settings/settings' });
      }
    }
  }
  </script>
  
  <style>
  .my-container {
    padding: 20px;
  }
  .title {
    font-size: 24px;
    font-weight: bold;
  }
  </style>