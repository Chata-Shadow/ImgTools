<template>
	<scroll-view class="container container-index" style="overflow-y: scroll;">
		<view v-if="SHOW_TIP">
			<add-tips :statusBarHeight="statusBarHeight" />
		</view>
		<view class="menu-list" :style="{'margin-top': statusBarHeight+40+'px' }">
			<view class="ad-container margin-top cu-list menu sm-border card-menu">
				<!-- <ad unit-id="adunit-28338c7d91d145af"></ad> -->
				<!-- <ad unit-id="adunit-7301464a68a1e24e" ad-type="video" ad-theme="white"></ad> -->
			</view>
			<view class="cu-card article" @click="addMask" >
				<view class="cu-item shadow" style="margin: 30rpx 30rpx 0rpx 30rpx; ">
					<view class="title">
						<view class="text-cut"> 图片压缩 </view>
					</view>
					<view class="content">
						<image style="width: 180rpx;" src="/static/image/logo/mask-logo.png" mode="aspectFill"></image>
						<view class="desc">
							<view class="text-content"> 在线图片压缩，可在线选择压缩比例和大小。</view>
							<view>
								<view class="grid justify-between">
									<view>
										<view class="cu-tag bg-red light sm round">图片压缩</view>
										<!-- <view class="cu-tag bg-green light sm round">保健康</view> -->
									</view>
									
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="cu-card article" @click="addSlogan">
				<view class="cu-item shadow" style="margin: 30rpx 30rpx 0rpx 30rpx; ">
					<view class="title">
						<view class="text-cut"> 武汉加油 </view>
					</view>
					<view class="content">
						<image style="width: 180rpx;"  src="/static/image/logo/slogan-logo.jpeg" mode="aspectFill"></image>
						<view class="desc">
							<view class="text-content">  武汉加油，中国加油，加油2020，不动如山，拒绝聚会，拒绝野味。</view>
							<view>
								<view class="grid justify-between">
									<view>
										<view class="cu-tag bg-red light sm round">武汉加油、自定义口号</view>
										<!-- <view class="cu-tag bg-green light sm round">自定义口号</view> -->
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="cu-card article" @click="addText">
				<view class="cu-item shadow" style="margin: 30rpx 30rpx 0rpx 30rpx; ">
					<view class="title">
						<view class="text-cut">  头像加字 </view>
					</view>
					<view class="content">
						<image style="width: 180rpx;"  src="/static/image/logo/text-logo.jpeg" mode="aspectFill"></image>
						<view class="desc">
							<view class="text-content">  头像一键加字，加V字，制作姓氏头像，让你在朋友圈脱颖而出。</view>
							<view>
								<view class="grid justify-between">
									<view>
										<view class="cu-tag bg-red light sm round">任意文字、颜色</view>
										<!-- <view class="cu-tag bg-green light sm round">多种颜色</view> -->
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="cu-card article" @click="chatBackground">
				<view class="cu-item shadow" style="margin: 30rpx 30rpx 0rpx 30rpx; ">
					<view class="title">
						<view class="text-cut">聊天背景图、壁纸锁屏 </view>
					</view>
					<view class="content">
						<image style="width: 180rpx;"  src="/static/image/logo/chat-bg-logo.png" mode="aspectFill"></image>
						<view class="desc">
							<view class="text-content"> 聊天背景图，高清手机壁纸，锁屏图片</view>
							<view>
								<view class="grid justify-between">
									<view>
										<view class="cu-tag bg-red light sm round">聊天背景、壁纸、锁屏</view>
										<!-- <view class="cu-tag bg-green light sm round">多种颜色</view> -->
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			
		</view>

	</scroll-view>
</template>

<script>
	import tuiIcon from "@/components/tui/icon";
	import addTips from "@/components/add-tips";
	
	// 在页面中定义插屏广告
	let interstitialAd = null;
	
	
	export default {
		components: {
			tuiIcon,
			addTips
		},
		data() {
			return {
				windowHeight: 0,
				statusBarHeight: 0,
				SHOW_TIP: false,
				rewardedVideoAdLoaded: false
			}
		},
		onLoad() {
			// 在页面onLoad回调事件中创建插屏广告实例
			// if (wx.createInterstitialAd) {
			// 	interstitialAd = wx.createInterstitialAd({
			// 		adUnitId: 'adunit-be801ba020f6edeb'
			// 	})
			// 	interstitialAd.onLoad(() => {})
			// 	interstitialAd.onError((err) => {
			// 		console.log(err);
			// 	})
			// 	interstitialAd.onClose(() => {})
			// }
			
		},
		onShow() {
			this.statusBarHeight = getApp().globalData.statusBarHeight;
			this.windowHeight = getApp().globalData.windowHeight;
			this.SHOW_TIP = getApp().globalData.SHOW_TIP;
			console.log(this.SHOW_TIP);
			
			// if (interstitialAd) {
			// 	interstitialAd.show().catch((err) => {
			// 		console.error(err)
			// 	})
			// }
		},
		onShareAppMessage() {
			return {
				title: '我换上了口罩头像，防止疫情蔓延，30款口罩、护目镜任你选！',
				desc: '防传染、戴口罩，从我做起！',
				imageUrl: '/static/image/mask/avatar_mask.png',
				path: '/pages/index/index',
				success: function(res) {
					console.log(res);
				}
			}
		},
		methods: {
			realtimeInfo: function() {
				wx.navigateToMiniProgram({
					appId: 'wx1656b2e5df4e587c',
					path: 'pages/index/index',
					success(res) {
						console.log(res);
					},
					fail(e) {
						console.log(e);
					}
				})
			},
			addMask: function() {
				uni.switchTab({
					url: '/pages/mask/add-mask'
				})
			},
			addSlogan: function(){
				uni.switchTab({
					url: '/pages/slogan/add-slogan'
				})
			},
			addText: function(){
				uni.navigateTo({
					url: '/pages/text/add-text'
				})
			},
			chatBackground: function(){
				uni.navigateTo({
					url: '/page-chat-bg/pages/index/index'
				})
			},
			
			handleContact: function(e) {
				console.log(e.detail.path)
				console.log(e.detail.query)
			}
		}
	}
</script>

<style scoped>
	.container-index{
		height: 2000rpx;
	}
	
	.logo-area{
		position: absolute;
		left: 20px;
	}
	.ad-container {
		width: 690rpx;
	}
	
	.about-actions{
		width: 690rpx;
	}

	.card-menu {
		margin-left: auto;
		margin-right: auto;
	}

	.free-btn-bordernone {
		background: none !important;
		color: #000 !important;
		display: inline-block !important;
	}

	.free-btn-bordernone::after {
		border: none;
	}
</style>
