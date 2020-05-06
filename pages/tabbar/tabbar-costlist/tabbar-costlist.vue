<template>
	<view class="content">
		
			<view class="flex-item flex-item-V ">
				<view class="uni-flex uni-column view-mine ">
				  
					   <view class="uni-flex uni-row">
						    <view class="flex-item bg-name-info">
							   <text class="content-head ">5月共花费：{{totalCost}}元	</text>
							</view>
					        <view class="flex-item uni-bg-green bg-name-info">
								<text class="task-content">记账{{count}}次</text>
							</view>
				     </view>
				  </view>
				</view>
<!-- 		<uni-grid :column="3">
			<uni-grid-item>
				<text class="text">文本</text>
			</uni-grid-item>
			<uni-grid-item>
				<text class="text">文本</text>
			</uni-grid-item>
			<uni-grid-item marker="image" :hor="35" :ver="-45" :img-width="25" src="https://img-cdn-qiniu.dcloud.net.cn/uni-ui/recommend.png">
				<text class="text">文本</text>
			</uni-grid-item>
		</uni-grid> -->
		 <view>
			<uni-list  v-for="(item,index) in resultList" :key="index">			
				<uni-list-item v-bind:title="item.title" v-bind:note="item.info" >		  
				</uni-list-item>  	   
			</uni-list>
		 </view>
	</view>
	 
	        
</template>

<script>
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	
	export default {
		  components: {uniGrid,uniGridItem,uniList,uniListItem},
 
		data() {
			return {
				title: 'Hello',			
				resultList:[],
				totalCost:0.0,
				count:0
					/*  {
						'billDesc':"张军杰",
						'price':'123.3'
					  } */							         
			}
			
		},
		created:function(){
		    this.getCostLists();
			this.getTotalCost();
		   },
		
		onLoad() {				 
		/* 	this.getCostLists(); */				 
		},
		methods: {
				routeChanged: function(){
					const that = this
						 console.log("1111" + that.$router.currentRoute.name);
				},
				getCostLists: function(){
					var vm = this;
					const requestTask = uni.request({
						method:'get',
						/* header: {
							//'Content-Type': 'application/x-www-form-urlencoded'
						        'content-type': 'application/json' //自定义请求头信息
						    }, */
					    url: 'http://localhost:8010/getBills', //仅为示例，并非真实接口地址。				
					    success: function(res) {			
						   console.log(res.data.length);
							for(var i = 0; i<res.data.length;i++){
								var resultItem = {};
								console.log(i);
								resultItem.info =  res.data[i].userName + " 时间：" + res.data[i].inTime;						
								resultItem.title = res.data[i].billDesc +"(" + res.data[i].price + "元)";		
								console.log(res.data);
								vm.resultList.push(resultItem);
								
							}
						/* 	vm.resultList = res.data;					 
					        console.log(vm.resultList); */
					    }
					});
				},
				getTotalCost: function(){
					var vm = this;
					const requestTask = uni.request({
						method:'get',			
					    url: 'http://localhost:8010/getTotalCost?yearMonth=2020-04', //仅为示例，并非真实接口地址。				
					    success: function(res) {			
							vm.totalCost = res.data[0].totalCost;
							vm.count = res.data[0].count;
							console.log(res.data.length);						
					    }
					});
				}
		}
	}
</script>

<style>
	.content {
		text-align: left;
		/* height: 800upx; */
		margin-top: 30upx;
	}
	.bg-view-mine {
		background-size: 100% 100%;
		margin: 80upx;
		height: 200upx;
	}
	
	 .costList{
		 height: 60%;
	 }
	
	.bg-name-info {
		background-size: 100% 100%;
		margin: 60upx;
	}
	.flex-item-V {
		width: 90%;
		height: 250upx;
		text-align: center;
		line-height: 150upx;
		border-radius: 10upx;
		margin: 4upx 34upx;
		background: linear-gradient(to right, #00aaff, #48ced0);
		color: #272b00;
		opacity: 0.7;
	}
</style>
