<template>
	<view class="content">
		<view class="staff">
			<view class="item">
				<view class="digit">10</view>
				<view class="word ">员工总数</view>
			</view>
			<view class="item">
				<view class="digit">10</view>
				<view class="word ">员工活跃数</view>
			</view>
			<view class="item">
				<view class="digit">10</view>
				<view class="word ">员工活跃数</view>
			</view>
		</view>
		<view class="client">
			<view class="nape leftTop leftbottom">
				<view class="digit wire  ">10</view>
				<view class="word wire">客户数</view>
			</view>
			<view class="nape ">
				<view class="digit wire">10</view>
				<view class="word wire ">正常车辆</view>
			</view>
			<view class="nape rightTop rightbottom">
				<view class="digit">10</view>
				<view class="word ">报废车辆</view>
			</view>
		</view>
		
		<view class="cat">
			<view class="client underline">
				<view class="nape leftTop ">
					<view class="digit wire  ">10</view>
					<view class="word wire">车辆已逾期</view>
				</view>
				<view class="nape ">
					<view class="digit wire">10</view>
					<view class="word wire ">七天内到期</view>
				</view>
				<view class="nape rightTop ">
					<view class="digit">10</view>
					<view class="word ">十五天内到期</view>
				</view>
			</view>
			<view class="client">
				<view class="nape  leftbottom">
					<view class="digit wire  ">10</view>
					<view class="word wire">一个月内到期</view>
				</view>
				<view class="nape ">
					<view class="digit wire">10</view>
					<view class="word wire ">两个月内到期</view>
				</view>
				<view class="nape  rightbottom">
					<view class="digit">10</view>
					<view class="word ">三个月内到期</view>
				</view>
			</view>
		</view>

		<view class="insurance">
			<view class="client underline">
				<view class="nape leftTop ">
					<view class="digit wire  ">10</view>
					<view class="word wire">车保已逾期</view>
				</view>
				<view class="nape ">
					<view class="digit wire">10</view>
					<view class="word wire ">七天内到期</view>
				</view>
				<view class="nape rightTop ">
					<view class="digit">10</view>
					<view class="word ">十五天内到期</view>
				</view>
			</view>
			<view class="client">
				<view class="nape  leftbottom">
					<view class="digit wire  ">10</view>
					<view class="word wire">一个月内到期</view>
				</view>
				<view class="nape ">
					<view class="digit wire">10</view>
					<view class="word wire ">两个月内到期</view>
				</view>
				<view class="nape  rightbottom">
					<view class="digit">10</view>
					<view class="word ">三个月内到期</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			uni.getStorage({
			    key: 'token',
			    success: function (res) {
			        console.log(res);
			    }
			});
		},
		methods: {

		}
	}
</script>

<style>
	.content {
		background-color: #e4e7ed;
		padding: 50rpx 25rpx;
		color: #60627e;
	}

	.staff {
		display: flex;
		justify-content: space-between;
		padding-bottom: 40rpx;
	}

	.item {
		width: 32%;
		padding: 40rpx 0;
		background-color: #FFFFFF;
		text-align: center;
		border-radius: 10rpx;
		color: #60627e;
	}

	.digit {
		font-size: 48rpx;
		padding-top: 20rpx;
		padding-bottom: 20rpx;
	}

	.word {
		padding-bottom: 20rpx;
		font-size: 18rpx;
	}

	.client {
		display: flex;
	}

	.nape {
		width: 33.5%;
		padding: 40rpx 0;
		background-color: #FFFFFF;
		text-align: center;
	}

	.wire {
		border-right: 1px solid #f1f3f5;
	}

	.leftTop {
		border-top-left-radius: 10rpx;
	}

	.leftbottom {
		border-bottom-left-radius: 10rpx;
	}

	.rightTop {
		border-top-right-radius: 10rpx;
	}

	.rightbottom {
		border-bottom-right-radius: 10rpx;
	}

	.cat,.insurance {
		padding-top: 40rpx;
	}

	.underline {
		border-bottom: 1px solid #f1f3f5;
	}
</style>
