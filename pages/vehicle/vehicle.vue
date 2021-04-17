<template>
	<view>
		<view class="box">
			<u-search placeholder="输入车牌号" v-model="keyword" :action-style="actionStyle"></u-search>
			<u-grid class="list" :col="4" :border="false">
				<u-grid-item>
					<u-icon name="car" :size="80"></u-icon>
					<view class="grid-text">全部</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="car" :size="80"></u-icon>
					<view class="grid-text">已车检</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="car" :size="80"></u-icon>
					<view class="grid-text">已逾期</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="car" :size="80"></u-icon>
					<view class="grid-text">7天内到期</view>
				</u-grid-item>
			</u-grid>
		</view>
		<view class="item">
			<view class="state">已逾期</view>
			<view class="subtitle">车牌号</view>
			<view class="license">湘E25678</view>
			<view class="master">车主 <text class="name">张先生</text></view>
			<view class="master">手机 <text class="phone">13412343232</text></view>
			<view class="details">查看详情
				<image class="little" src="../../static/right.png" mode="widthFix"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				keyword: "",
				actionStyle: {
					'background-color': '#19be6b',
					'color': '#FFFFFF',
					'width': '100rpx',
					'height': '60rpx',
					'line-height': '60rpx',
					'border-radius': '10rpx'
				},
				token: "",
			}
		},
		methods: {

		},
		onLoad() {
			let tokens = "";
			uni.getStorage({
				key: 'token',
				success: function(res) {
					tokens = res.data;
				}
			});
			this.token = tokens
		},
		onReady() {

			uni.request({
				url: "http://106.54.87.27:8081/manager/insuranceRecord/addInsuranceRecord",
				method: "POST",
				data: {},
				header: {
					'content-type': 'application/json', //自定义请求头信息
					"token": this.token
				},
				success: (res) => {
					console.log(res)
				}
			})
		},
	}
</script>

<style>
	page {
		background-color: #f6f6f6;
	}

	.box {
		padding: 80rpx 80rpx;
		background-color: #FFFFFF;
	}

	.list {
		padding-top: 60rpx;
	}

	.item {
		box-sizing: border-box;
		width: 95%;
		padding: 0 8rpx;
		margin: 30rpx auto 0;
		background-color: #FFFFFF;
		border-radius: 20rpx;
		text-indent: 10rpx;
	}

	.state {
		border-bottom: 1rpx solid #e5e5e5;
		height: 50rpx;
		line-height: 50rpx;
		font-size: 24rpx;
	}

	.subtitle {
		padding-top: 40rpx;
		text-align: center;
		color: #a2a2a2;
		font-size: 32rpx;
	}

	.license {
		text-align: center;
		font-size: 48rpx;
		font-weight: bold;
		padding-bottom: 40rpx;
	}

	.master {
		font-size: 36rpx;
		color: #a2a2a2;
	}

	.name {
		color: #000000;
		padding-left: 30rpx;
	}

	.phone {
		font-size: 28rpx;
		color: #6170fa;
		padding-left: 30rpx;
	}

	.details {
		border-top: 1rpx solid #e5e5e5;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 20rpx 80rpx 0;
	}

	.little {
		width: 30rpx;
	}
</style>
