<template>
	<view>
		<view class="search">
			<txl @ev="evFunc" :datas="datas" color="red" :index="true" name="employeeName"></txl>
		</view>
	</view>
</template>

<script>
	import txl from '@/components/yt-txl/index.vue';
	export default {
		components: {
			txl
		},
		data() {
			return {
				datas: [],
				token: "",
				keyword: '',
				scrollTop: 0,
			}
		},
		methods: {
			evFunc(data) {
				console.log(data)
			}
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
				url: "http://106.54.87.27:8081/staff/staffList",
				method: "GET",
				data: {},
				header: {
					'content-type': 'application/json', //自定义请求头信息
					"token": this.token
				},
				success: (res) => {
					let THIS = this.datas;
					 console.log(res)
					res.data.data.forEach(
						function(value, index, array) {
							console.log(value)
							THIS.push({
								"employeeId": "test1",
								"employeeName": value.staffName,
								"companyId": "1",
								"companyName": "test company",
								"departmentId": "testdeptid",
								"departmentName": value.staffPhone,
								"postId": "testpostid",
								"postName": "testpost",
							})
						}
					)
					console.log(res.data.data)


				}
			})
		}
	}
</script>

<style>
	page {
		background-color: #F4F4F4;
	}

	.search {}

	.frame {}

	.message {
		padding: 0 100rpx 0 40rpx;
		background-color: #f4f4f4;
	}

	.list-cell {
		background-color: #FFFFFF;
		padding: 20rpx 40rpx;
		display: flex;
		margin-bottom: 10rpx;
	}

	.surname {
		margin-right: 40rpx;
		width: 100rpx;
		height: 100rpx;
		line-height: 100rpx;
		background-color: #DD524D;
		border-radius: 50%;
		font-size: 40rpx;
		color: #FFFFFF;
		text-align: center;
		font-family: 'Courier New', Courier, monospace;
	}

	.details {
		line-height: 50rpx;
	}
</style>
