<template>
	<view>
		<form @submit="loginSubmit">
			<view  class="login-banner">
				<label class="login-text">欢迎登录-主人~</label>
			</view>
			<view class="uni-form-item uni-column">
				<input class="uni-input boder_line" name="username" placeholder="请输入账号">
				</input>
				<input class="uni-input boder_line" name="password" placeholder="请输入密码">
				</input>
				
			</view>
			<view class="login_gap">
				<button type="primary" form-type="submit">登录</button>
		   </view>
		   	<view   class="register-link-wrapper">
				<label class="uni-link register-link">没有账户，去注册</label>			 
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			loginSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				var formdata = e.detail.value	
				const requestTask = uni.request({
					method: 'POST',
					header: {
						'Content-Type': 'application/x-www-form-urlencoded'
						//'content-type': 'application/json' //自定义请求头信息
					},
					url: 'http://localhost:8010/login', //仅为示例，并非真实接口地址。
					data: {						
						userName: e.detail.username,
						psw:e.detail.password,					 
						inTime: "2020-05-05 13:32"
					},
					success: function(res) {
						console.log(res.data);
						 uni.switchTab({							 
						     url:'/pages/tabbar/tabbar-home/tabbar-home'
						 });			 
					}
				});
			},
		}
	}
</script>

<style>
.login-banner{
	display: flex;
	margin: 16upx 10px; 
	padding: 14% 60upx;
	
	/* background-color: #00b3ff; */
	background: linear-gradient(to right, rgba(102, 145, 255, 1),#00b3ff);
	border-radius: 30upx;
	}
	.login-text{
		width: 100%;
		text-align: center;
		font-size:20px;
		display: flex;
		font-weight: 800;
		color: #ffffff;	
		margin: 0 10%;
	}
	.boder_line{
		border-bottom: 2upx solid;
		border-color: #eee;
	}
	.register-link{
	 
		font-size:small;		
		font-weight: 600;	 
		margin:0 auto;
		/* margin: 0 50%; */
	}
	.login_gap{
	padding: 30px 16px;
	}
	
	.register-link-wrapper{
		line-height: 40px;
		height: 100upx;
		padding: 30upx;	 
		text-align: center;	 
	}
	page{
		height: 100%;
	}
</style>
