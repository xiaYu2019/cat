<template>
	<view>
		<image class="bg" src="../../static/log.png" mode="heightFix"></image>
		<view class="login">
			<u-form class="form" :model="form" ref="uForm">
				<u-form-item prop="staffPassword">
					<u-input v-model="form.staffPassword" placeholder="请输入手机号" />
				</u-form-item>
				<u-form-item prop="staffPhone">
					<u-input v-model="form.staffPhone" type="password" placeholder="请输入密码" />
				</u-form-item>
				<u-button class="bt" @click="submit" type="primary">登录</u-button>
			</u-form>
		</view>
		<u-toast ref="uToast" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				form: {
					staffPassword: '',
					staffPhone: '',
				},
				rules: {
					staffPassword: [{
							required: true,
							message: '请输入手机号',
							trigger: ['blur'],
						},
						{
							validator: (rule, value, callback) => {
								// 调用uView自带的js验证规则，详见：https://www.uviewui.com/js/test.html
								return this.$u.test.mobile(value);
							},
							message: '手机号码不正确',
							// 触发器可以同时用blur和change，二者之间用英文逗号隔开
							trigger: ['change', 'blur'],
						}
					],
					staffPhone: [{
							required: true,
							message: '请输入密码',
							trigger: ['change', 'blur'],
						}
						// ,
						// {
						// 	// 正则不能含有两边的引号
						// 	pattern: /^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z]+\S{5,12}$/,
						// 	message: '需同时含有字母和数字，长度在6-12之间',
						// 	trigger: ['change', 'blur'],
						// }
					]
				}
			}
		},
		methods: {
			
			submit() {
				this.$refs.uForm.validate(valid => {
					if (valid) {
						console.log(valid)
						uni.request({
							url: 'http://106.54.87.27:8081/staff/login', //仅为示例，并非真实接口地址。
							method: "POST",
							data: {
								staffPhone: this.form.staffPassword,
								staffPassword: this.form.staffPhone,
							},
							header: {
								'content-type': 'application/json' //自定义请求头信息
							},
							success: (res) => {
								if (res.data.code == 0) {
									
									this.$refs.uToast.show({
										title: '登录成功',
										type: 'success',
										isTab:true,
										duration:1000,
										url: 'pages/index/index'
									}),
									//设置tokui
									uni.setStorage({
										key: 'token',
										data: res.data.data.token,
										success: function() {
											console.log("设置成功");
										}
									});
								} else {
									console.log("出错");
								}

								//登录

							},
						});

					} else {

					}
				});
			}
		},
		onReady() {
			this.$refs.uForm.setRules(this.rules);
		}
	}
</script>

<style>
	.bg {
		font-size: 0;
		vertical-align: bottom;
	}

	.login {
		padding: 200rpx 60rpx;
		background-color: #007AFF;
	}

	.form {
		background-color: #FFFFFF;
		padding: 20rpx 80rpx;
	}

	.bt {
		margin-top: 20rpx;
	}
</style>
