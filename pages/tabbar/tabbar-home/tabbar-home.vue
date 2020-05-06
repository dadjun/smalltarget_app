<template>
	<view class="content">
		<text class="title-task">今日目标:</text>
		<view class="uni-padding-wrap uni-common-mt">

			<!--  <view class="uni-title uni-common-mt">
             	flex-direction: column
             	<text>\n纵向布局</text>
             </view> -->
			<view class="uni-flex uni-column">
				<view class="flex-item flex-item-V ">
					<view class="uni-flex uni-column bg-runner ">
						<text class="content-head ">跑步： </text>
						<text class="task-content">2km/10km</text>
						<view class="progress-box">
							<progress percent="20" active stroke-width="6" activeColor="#09BB07" backgroundColor="#F76260" />
						</view>
					</view>
				</view>

				<text class="title-task ">本周学习目标:</text>
				<view class="flex-item flex-item-V bg-runner">
					<text class="content-head">背单词： </text>
					<text class="task-content">2个/100个</text>
					<view class="progress-box">
						<progress percent="20" active stroke-width="6" activeColor="#09BB07" backgroundColor="#F76260" />
					</view>
				</view>
			</view>


		</view>
		<!--     <view class="uni-flex uni-bg-padding">
				 </view>	 -->

	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index: 0,
				scrollTop: 0,
				old: {
					scrollTop: 0
				},

			}
		},
		onLoad() {},
		methods: {
			bindPickerChange(e) {
				console.log(e)
			},
			upper: function(e) {
				console.log(e)
			},
			lower: function(e) {
				console.log(e)
			},
			scroll: function(e) {
				console.log(e)
				this.old.scrollTop = e.detail.scrollTop
			},
			goTop: function(e) {
				this.scrollTop = this.old.scrollTop
				this.$nextTick(function() {
					this.scrollTop = 0
				});
				uni.showToast({
					icon: "none",
					title: "纵向滚动 scrollTop 值已被修改为 0"
				})
			}
		}
	};
</script>

<style>
	.content {
		text-align: center;
		height: 200upx;
		margin-top: 60upx;
	}

	@font-face {
		font-family: 'iconfont';
		src: url('https://at.alicdn.com/t/font_865816_17gjspmmrkti.ttf') format('truetype');
	}

	.test {
		font-family: iconfont;
		margin-left: 20rpx;
	}

	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
	}



	.scroll-view-item_H {
		display: inline-block;
		width: 100%;
		height: 300upx;
		line-height: 300upx;
		text-align: center;
		font-size: 36upx;
	}

	.flex-item {
		width: 33.3%;
		height: 200upx;
		text-align: center;
		line-height: 200upx;
	}

	.flex-item-V {
		width: 85%;
		height: 250upx;
		text-align: center;
		line-height: 150upx;
		border-radius: 26upx;
		margin: 30upx;
		background: linear-gradient(to right, blue, rgba(102, 145, 255, 1));

		color: #FFB400;
		opacity: 0.7;
	}

	.uni-bg-padding {
		width: 100%;
		height: 100upx;
		background: #FFB400;
		color: #FFF;
	}

	.uni-task-bg {
		background: #F4F5F6;
		color: #FFF;
	}

	.title-task {
		text-align: left;
		color: #576B95;
		font-size: 18px;
		display: flex;
		flex-direction: row;

		font-weight: 600;
		padding: 12upx;
	}

	.content-head {
		text-align: left;
		color: #FFFFFF;
		font-size: 16px;
		font-weight: 600;
		padding: 12upx;

	}

	.task-content {
		font-size: 16px;
		color: #F1F1F1;
		padding-left: 20upx;
		text-align: left;
	}

	.bg-runner {
		background-size: 100% 100%;

	}
</style>
