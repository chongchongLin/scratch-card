<template>
	<view class="content">
		<view class="list">
			<view class="item" v-for="(item,index) in list" :key=item.id>
					<view class="pic">
						<image src="../../static/刮刮乐.jpeg" mode=""></image>
					</view>
				<view class="item-content scratch-font" v-if="item.show">
					{{item.name}}
				</view>
				<view class="item-content " v-else @click="getAward(item.id)">
					 刮一刮
				</view>
			</view>
		</view>
<!-- 		<view class="randomBtn" @click="random()">
			打乱顺序
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[{id:0,name:'一块橡皮擦'},{id:1,name:'一根铅笔'},{id:2,name:'一根棒棒糖'},
				{id:3,name:'免写卡'},{id:4,name:'谢谢惠顾'},{id:5,name:'试卷大礼包'},
				{id:6,name:'一包辣条'},{id:7,name:'免背卡'},{id:8,name:'一支黑笔'}]
			}
		},
		onLoad() {
			this.init()
		},
		methods: {
			init(){
				this.list = this.list.map((item)=>({...item,show:false}))
			},
			getAward(index){
				console.log(index)
				for(let child of this.list){
					if(child.id == index){
						child.show = true
					}else{
						// child.show = false
					}
				}
				
			},
			random(){
				this.randomList(this.list)
				console.log(this.list)
			},
			randomList(arr){
				for (let i = arr.length-1; i >=0; i--) {
				   let randomIndex = Math.floor(Math.random()*(i+1));
				    let itemAtIndex = arr[randomIndex];
				    arr[randomIndex] = arr[i];
				    arr[i] = itemAtIndex;
				}
			}
		}
	}
</script>

<style lang="scss">
		
	image{
		width: 100%;
		height: 100%;
	}
	.content {
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.list{
		width: 100%;
		display: grid;
		grid-template-columns: repeat(3,33%);
		grid-gap: 12rpx;
		.item{
			height: 240rpx;
			border: 1rpx solid black;
			display: flex;
			flex-direction: column;
			align-items: center;
			background: #e40100;
			.pic{
				width: 100%;
				height: 100rpx;
			}
			.item-content{
				width: 80%;
				height: 100rpx;
				background: #999;
				display: flex;
				align-items: center;
				justify-content: center;
				box-sizing: border-box;
				padding: 12rpx;
			}
			.scratch-font{
				font-size: 24rpx;
			}
		}
	}
	.randomBtn{
		width: 200rpx;
		height: 80rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 1rpx solid red;
		margin-top: 24rpx;
	}
	
</style>
