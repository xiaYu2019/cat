<template>
	<view>
		<view class="upper">
			<view class="role">
				<view class="picture">超</view>
				<view class="characters">
					<view class="post">超级管理员</view>
					<view class="phone">12345678998</view>
				</view>
			</view>
			<u-grid :col="3" :border="false" class="classify">
				<u-grid-item bg-color="transparent">
					<u-icon name="man-add" :size="80"></u-icon>
					<view class="grid-text">员工管理</view>
				</u-grid-item>
				<u-grid-item bg-color="transparent" @click="skip">
					<u-icon name="car" :size="80"></u-icon>
					<view class="grid-text">车检管理</view>
				</u-grid-item>
				<u-grid-item bg-color="transparent">
					<u-icon name="rmb-circle" :size="80"></u-icon>
					<view class="grid-text">客户管理</view>
				</u-grid-item>
			</u-grid>
			<u-grid :col="4" :border="false" class="grouping">
				<u-grid-item>
					<u-icon name="grid" :size="80" color="#007AFF"></u-icon>
					<view class="grid-text">模块管理</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="edit-pen" :size="80" color="#007AFF"></u-icon>
					<view class="grid-text">签名管理</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="clock" :size="80" color="#007AFF"></u-icon>
					<view class="grid-text">定时管理</view>
				</u-grid-item>
				<u-grid-item>
					<u-icon name="file-text" :size="80" color="#007AFF"></u-icon>
					<view class="grid-text">事件管理</view>
				</u-grid-item>
			</u-grid>
		</view>

		<view class="hyperlink">
			<view class="item">
				<view class="bg">
					<image class="ph" src="../../static/shield.png" mode=""></image>
				</view>
				<view> 保险公司</view>
				<image  class="right" src="../../static/right.png" mode="widthFix"></image>
			</view>
			<view class="item">
				<view class="bg time">
					<image class="ph" src="../../static/time.png" mode=""></image>
				</view>
				<view>提醒间隔</view>
				<image  class="right" src="../../static/right.png" mode="widthFix"></image>
			</view>
			<view class="item">
				<view class="bg cat">
					<image class="ph" src="../../static/cat.png" mode=""></image>
				</view>
				<view> 车辆类型</view>
				<image  class="right" src="../../static/right.png" mode="widthFix"></image>
			</view>
			<view class="item">
				<view class="bg jurisdiction">
					<image class="ph" src="../../static/jurisdiction.png" mode=""></image>
				</view>
				<view> 权限管理</view>
				<image  class="right" src="../../static/right.png" mode="widthFix"></image>
			</view>
			<view class="item ">
				<view class="bg cat">
					<image class="ph" src="../../static/calendar.png" mode=""></image>
				</view>
				<view> 节日管理</view>
				<image  class="right" src="../../static/right.png" mode="widthFix"></image>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		components: {},
		data() {
			return {

			}
		},
		onLoad() {},

		methods: {
			skip(){
				uni.navigateTo({
					url:"../vehicle/vehicle"
				})
			}
		}
	}
</script>

<style>
	.upper {
		background-color: #007AFF;
		padding: 40rpx 20rpx;
	}

	.role {
		color: #FFFFFF;
		padding: 0 40rpx;
		display: flex;
	}

	.picture {
		width: 140rpx;
		height: 140rpx;
		border-radius: 50%;
		background-color: #47b3db;
		font-size: 48rpx;
		text-align: center;
		line-height: 140rpx;
	}

	.characters {
		padding-left: 50rpx;
	}

	.post {
		height: 50%;
		padding-top: 20rpx;
		font-size: 40rpx;
	}

	.phone {
		font-size: 12rpx;
		color: #c0c0c0;
	}

	.classify {
		color: #FFFFFF;
	}

	.grouping {
		color: #80809f;
	}

	.item{
		padding: 10rpx  40rpx;
		display: flex;
		align-items:center;
		border-bottom:  1rpx solid #f4f6f8;
	}
	.bg {
		margin-right: 40rpx;
		box-sizing: border-box;
		padding-top: 10rpx;
		width: 60rpx;
		height: 60rpx;
		border-radius: 50%;
		background-color: #fbeee7;
		text-align: center;
	}
	.time{
		background-color: #ebf0fc;
	}
	.cat{
		background-color: #fbeaf2;
	}
	.jurisdiction{
		background-color: #fff9e3;
	}
	
	.ph{
		width: 40rpx;
		height: 40rpx;
	}
	.right{
		margin-left: 420rpx;
		width:40rpx;
	}
</style>
