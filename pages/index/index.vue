<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}---{{age}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello...every_body',
				age:18
			}
		},
		onLoad(){
			let res = global.isLogin();
			if(!res){
				uni.showModal({
					title: '提醒',
					content: '请先登录',
					// showCancel: true,
					cancelText: '取消',
					confirmText: '确定',
					success: res => {
						if(res.confirm){
							console.log('用户点击了确定')
							uni.navigateTo({
								url: '/pages/login/login',
								success: res => {
									
								},
								fail: () => {
									
								},
								complete: () => {}
							});
						}else{
							console.log('用户点击了取消')
						}
					}
				});
			}
		// 	console.log('onload');
		// 	setTimeout(() =>{
		// 		this.age = 20;
		// 	},1000)
		// 	uni.showLoading({
		// 		title:"你好啊",
		// 		// icon:'success'
		// 		mask:true
		// 	})
		// 	setTimeout(function() {
		// 		uni.hideLoading()
		// 	}, 1000);
		// },
		},
		methods: {
			
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
