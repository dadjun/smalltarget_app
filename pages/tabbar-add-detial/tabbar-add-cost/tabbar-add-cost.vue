<template>
	<view class="content">
		<view>
			
			<form @submit="formSubmit" @reset="formReset">
				<view class="uni-padding-wrap uni-common-mt">
				<!-- 	<view class="myinput uni-flex uni-row"> -->
					<!-- 	<view class="uni-label  flex-item">请选择类型: </view> -->
				 	<view class="flex-item">
						   
							 <view class="uni-list">
								 <view class="uni-title uni-common-mt uni-common-pl text1">请选择类型:</view>
								 <radio-group @change="radioChange">
									 <label class="uni-list-cell uni-list-cell-pd" v-for="(item, index) in items" :key="item.value">
										 <view>
											 <radio :value="item.value" :checked="index === current" />
										 </view>
										 <view>{{item.name}}</view>
									 </label>
								 </radio-group>
							 </view>				 
				</view>

					<!-- <view class="mygap flex-item-V"></view> -->
					<view class="uni-flex uni-row flex-item-V">
						<view class="myinput uni-label  flex-item">请填写费用: </view>
						<view class="title flex-item">
							<input class="uni-input " name="price" placeholder="请输入费用" />
						</view>
					</view>

					<view class="mygap uni-bg-padding flex-item-V"></view>
					<view class="uni-btn-v flex-item-V">
						<button type="primary" form-type="submit">保存</button>
					<!-- 	<button type="default" form-type="reset">取消</button> -->
					</view>
				</view>
			</form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				 items: [ {
							value: 'food',
							name: '买菜'
						 },
						 {
							value: 'commodity',
							name: '日用品',
							checked: 'true'
						 },
						 {
							value: 'gas',
							name: '煤气'
						 },
						 ],
					 current: 0
				 }
		},
		onLoad() {

		},
		methods: {
			radioChange: function(evt) {
			            for (let i = 0; i < this.items.length; i++) {
			                if (this.items[i].value === evt.target.value) {
			                    this.current = i;
			                    break;
			                }
			            }
			        },
				
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				var formdata = e.detail.value
				/*      uni.showModal({
				          content: '表单数据内容：' + JSON.stringify(formdata),
				          showCancel: false
				      }); */
				const requestTask = uni.request({
					method: 'POST',
					header: {
						'Content-Type': 'application/x-www-form-urlencoded'
						//'content-type': 'application/json' //自定义请求头信息
					},
					url: 'http://localhost:8010/putBills', //仅为示例，并非真实接口地址。
					data: {
						price: e.detail.value.price,
						userName: "张军杰·",
						billDesc:this.items[this.current].name,
						billType: e.detail.value.type,
						billName: "嘿嘿",
						inTime: ""
					},
					success: function(res) {
						console.log(res.data);
						 uni.switchTab({
							 
						     url:'/pages/tabbar/tabbar-costlist/tabbar-costlist'
						 });
						 
			 
					}
				});
			},
			formReset: function(e) {
				console.log('清空数据')
			}
		}
	}
</script>

<style>
	.content {
		text-align: left;
		height: 400upx;
		margin-top: 100upx;
	}

	.mygap {
		text-align: center;
		height: 12upx;
		background-color: #e3e3e3;
		margin-top: 2upx;
	}

	.myinput {
		height: 380upx;
		padding: 16upx 8px;
	}
	
	.text1{
		text-align: left;
		margin-left: 100px;
	}
</style>
