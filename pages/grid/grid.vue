<template>
	<view class="grid-container">
		<text class="title">战队信息</text>
		<uni-grid>
			<uni-grid-item v-for="(team, index) in teamList" :key="index" @click="viewTeam(team)">
				<text>{{ team.name }}</text>
				<text>排名: {{ team.rank }}</text>
			</uni-grid-item>
		</uni-grid>
	</view>
</template>

<script>
export default {
	data() {
		return {
			teamList: [
				{ name: '战队A', rank: 1 },
				{ name: '战队B', rank: 2 },
				// 更多战队...
			]
		};
	},
	methods: {
		viewTeam(team) {
			// 查看战队详情的逻辑
			uni.navigateTo({ url: `/pages/team-detail/team-detail?id=${team.id}` });
		}
	}
}
</script>

<style>
.grid-container {
	padding: 20px;
}
.title {
	font-size: 24px;
	font-weight: bold;
}
</style>
