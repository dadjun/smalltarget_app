<template>
	<view>
		<form @submint="formSubmit">
			<view  class="register-banner">
				<label class="register-text">小当家</label>
			</view>
			<view class="uni-form-item uni-column">
				<input class="uni-input" name="username" placeholder="请输入账号">
				</input>
				<input class="uni-input" name="password" placeholder="请输入密码">
				</input>
				<input class="uni-input" name="password" placeholder="请再次输入密码">
				</input>
				
			</view>
		   <button type="primary" plain="true">注册</button>
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
			
		}
	}
</script>

<style>
	.register-banner{
		display: flex;
		margin: 16upx 10px; 
		padding: 16% 60upx;
		
		background-color: #00AAFF;
		border-radius: 20upx;
		}
		.register-text{
			width: 100%;
			text-align: center;
			font-size: large;
			display: flex;
			font-weight: 800;
			color: #C0C0C0;	
			margin: 0 40%;
		}
		
		.register-link{
		 
			font-size:small;		
			font-weight: 600;	 
			margin:0 auto;
			/* margin: 0 50%; */
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
