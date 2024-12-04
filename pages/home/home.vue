<template>
  <view class="home-container">
    <text class="title">欢迎使用 SU Team 管理系统</text>
    <text class="description">
      这是一个基于 UniApp 的战队管理系统，您可以在这里查看战队信息、动态和成员状态。
    </text>
    <button @click="navigateToDynamic">查看动态</button>
    <button @click="navigateToTeam">查看战队</button>
  </view>
</template>

<script>
export default {
  methods: {
    navigateToDynamic() {
      uni.navigateTo({ url: '/pages/dynamic/dynamic' });
    },
    navigateToTeam() {
      uni.navigateTo({ url: '/pages/team/team' });
    }
  }
}
</script>

<style>
.home-container {
  padding: 20px;
  text-align: center;
}
.title {
  font-size: 24px;
  font-weight: bold;
}
.description {
  margin: 20px 0;
}
button {
  margin: 10px;
}
</style>
