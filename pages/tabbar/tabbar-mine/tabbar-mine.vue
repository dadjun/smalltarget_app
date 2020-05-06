<template>
	<view class="content">
		<view class="uni-flex uni-column">
			<view class="flex-item flex-item-V ">
				<view class="uni-flex uni-column view-mine ">
				  
					   <view class="uni-flex uni-row">
						    <view class="flex-item bg-name-info">
							   <text class="content-head ">用户名：dadjun	</text>
							</view>
					        <view class="flex-item uni-bg-green bg-name-info">
								<text class="task-content">已连续记账100天</text>
							</view>
				     </view>
				</view>
				<view  class="uni-flex uni-column">
					   <uni-list-item title="我的信息"></uni-list-item>
					   <uni-list-item title="修改密码"></uni-list-item>
					   <uni-list-item title="退出登录"></uni-list-item>
				</view>
			</view>

		</view>
	 
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
 	
	export default {
		components: {uniList,uniListItem},
		data() {
			return {
				title: 'Hello',
				 dataList: [{id: "1", name: '我的信息'}, {id: "2", name: '修改密码'}, {id: "3", name: '退出'}]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
		margin-top: 30upx;
	}

	.bg-view-mine {
		background-size: 100% 100%;
		margin: 80upx;
		height: 200upx;
	}

 
	
	.bg-name-info {
		background-size: 100% 100%;
		margin: 80upx;
	}
	
	
	.flex-item-V {
		width: 85%;
		height: 250upx;
		text-align: center;
		line-height: 150upx;
		border-radius: 36upx;
		margin: 30upx;
		background: linear-gradient(to right, blue, rgba(102, 145, 255, 1));
		color: #FFB400;
		opacity: 0.7;
	}
</style>
