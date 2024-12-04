<template>
  <div>
    <uni-nav-bar title="战队管理" :fixed="true" :border="true" :shadow="true">
      <template v-slot:left>
        <uni-icons type="arrow-left" @click="goBack" />
      </template>
    </uni-nav-bar>
    <router-view></router-view>
    <div class="tabbar">
      <router-link to="pages/home" class="tab-item">首页</router-link>
      <router-link to="pages/gird" class="tab-item">动态</router-link>
      <router-link to="pages/team" class="tab-item">战队</router-link>
      <router-link to="pages/my" class="tab-item">我的</router-link>
    </div>
  </div>
</template>

<script>
	import initApp from '@/common/appInit.js';
	import openApp from '@/common/openApp.js';
	// #ifdef H5
		openApp() //创建在h5端全局悬浮引导用户下载app的功能
	// #endif
	import checkIsAgree from '@/pages/uni-agree/utils/uni-agree.js';
	import uniIdPageInit from '@/uni_modules/uni-id-pages/init.js';
	export default {
		globalData: {
			searchText: '',
			appVersion: {},
			config: {},
			$i18n: {},
			$t: {}
		},
		onLaunch: function() {
			console.log('App Launch')
			this.globalData.$i18n = this.$i18n
			this.globalData.$t = str => this.$t(str)
			initApp();
			uniIdPageInit()
			
			// #ifdef APP
			//checkIsAgree(); APP端暂时先用原生默认生成的。目前，自定义方式启动vue界面时，原生层已经请求了部分权限这并不符合国家的法规
			// #endif

			// #ifdef H5
			// checkIsAgree(); // 默认不开启。目前全球，仅欧盟国家有网页端同意隐私权限的需要。如果需要可以自己去掉注视后生效
			// #endif

			// #ifdef APP
			//idfa有需要的用户在应用首次启动时自己获取存储到storage中
			/*var idfa = '';
			var manager = plus.ios.invoke('ASIdentifierManager', 'sharedManager');
			if(plus.ios.invoke(manager, 'isAdvertisingTrackingEnabled')){
				var identifier = plus.ios.invoke(manager, 'advertisingIdentifier');
				idfa = plus.ios.invoke(identifier, 'UUIDString');
				plus.ios.deleteObject(identifier);
			}
			plus.ios.deleteObject(manager);
			console.log('idfa = '+idfa);*/
			// #endif
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		methods: {
			goBack() {
				// 返回上一页的逻辑
				uni.navigateBack();
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
	.tabbar {
		display: flex;
		justify-content: space-around;
		background-color: #f8f8f8;
		padding: 10px 0;
		position: fixed;
		bottom: 0;
		width: 100%;
	}
	.tab-item {
		text-decoration: none;
		color: #333;
		flex: 1;
		text-align: center;
	}
</style>
