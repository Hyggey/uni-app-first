<template>
	<view>
		<!-- #ifdef MP-WEIXIN -->
			<button type="primary" open-type="getUserInfo" @getuserinfo="getUserInfo" withCredentials="true">
				微信登录
			</button>
		<!-- #endif -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			getUserInfo(res){
				if(!res.detail.iv){
					uni.showToast({
						title:'你取消了授权,登录失败',
						icon:'none'
					})
					return false
				}else{
					console.log(res)
				}
				uni.login({
					success: res1 =>{
						console.log(res1)
						// https://api.weixin.qq.com/sns/jscode2session?appid=APPID&secret=SECRET&js_code=JSCODE&grant_type=authorization_code
						uni.request({
							url:'https://api.weixin.qq.com/sns/jscode2session',
							data:{
								appid:'wx7b3d9028f105a482',
								secret:'521daca444ae0648bbea1e7301f56739',
								js_code:res1.code,
								grant_type:'authorization_code'
							},
							success: res2 =>{
								console.log(res2)
							}
						})
					}
				})
			}
		}
	}
</script>

<style>

</style>
