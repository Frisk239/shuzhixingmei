<template>
	<view class="login-container">
		<!-- 登录表单 -->
		<view class="form-section">
			<!-- 平台标题 -->
			<view class="platform-title-section">
				<text class="platform-title">青梅产业平台</text>
			</view>

			<!-- 手机号输入 -->
			<view class="input-group">
				<view class="input-icon">📱</view>
				<input
					v-model="phoneNumber"
					class="input-field"
					type="number"
					placeholder="请输入手机号"
					maxlength="11"
				/>
			</view>

			<!-- 验证码输入 -->
			<view class="input-group">
				<view class="input-icon">💬</view>
				<input
					v-model="verificationCode"
					class="input-field"
					type="number"
					placeholder="请输入验证码"
					maxlength="6"
				/>
				<button
					class="get-code-btn"
					:disabled="countdown > 0"
					@click="getVerificationCode"
				>
					{{ countdown > 0 ? `${countdown}秒` : '获取验证码' }}
				</button>
			</view>

			<!-- 密码设置 -->
			<view class="input-group">
				<view class="input-icon">🔒</view>
				<input
					v-model="password"
					class="input-field"
					type="password"
					placeholder="请设置密码"
				/>
			</view>
		</view>

		<!-- 注册按钮 -->
		<view class="register-section">
			<button class="register-btn" @click="handleRegister">
				注册
			</button>
		</view>

		<!-- 底部链接 -->
		<view class="footer-section">
			<text class="footer-text">已有账号？</text>
			<text class="login-link" @click="goToLogin">去登录</text>
		</view>
	</view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const phoneNumber = ref('')
const verificationCode = ref('')
const password = ref('')
const countdown = ref(0)

// 获取验证码
const getVerificationCode = () => {
	if (!phoneNumber.value || phoneNumber.value.length !== 11) {
		uni.showToast({
			title: '请输入正确的手机号',
			icon: 'none'
		})
		return
	}

	// 模拟获取验证码
	countdown.value = 60
	const timer = setInterval(() => {
		countdown.value--
		if (countdown.value <= 0) {
			clearInterval(timer)
		}
	}, 1000)

	uni.showToast({
		title: '验证码已发送',
		icon: 'success'
	})
}

// 处理注册
const handleRegister = () => {
	if (!phoneNumber.value || !verificationCode.value || !password.value) {
		uni.showToast({
			title: '请填写完整信息',
			icon: 'none'
		})
		return
	}

	// 模拟注册成功，直接跳转到首页
	uni.showToast({
		title: '注册成功',
		icon: 'success'
	})

	setTimeout(() => {
		uni.navigateTo({
			url: '/pages/index/index'
		})
	}, 1500)
}

// 去登录（模拟登录成功）
const goToLogin = () => {
	uni.showToast({
		title: '登录成功',
		icon: 'success'
	})

	setTimeout(() => {
		uni.navigateTo({
			url: '/pages/index/index'
		})
	}, 1000)
}
</script>

<style scoped>
.login-container {
	min-height: 750px;
	background: url('/static/background.png') no-repeat center center;
	background-size: cover;
	padding: 40px 20px;
	display: flex;
	flex-direction: column;
	justify-content: center;
}

.header-section {
	padding: 60px 0 40px;
	text-align: center;
}

.main-title {
	font-size: 24px;
	font-weight: bold;
	color: #52c41a;
}

.login-title-section {
	text-align: center;
	margin-bottom: 40px;
}

.login-title {
	display: block;
	font-size: 32px;
	font-weight: bold;
	color: #333;
	margin-bottom: 10px;
}

.platform-title {
	display: block;
	font-size: 24px;
	font-weight: bold;
	color: #333;
}

.form-section {
	margin-bottom: 40px;
}

.platform-title-section {
	text-align: center;
	margin-bottom: 30px;
}

.platform-title {
	font-size: 24px;
	font-weight: bold;
	color: #52c41a;
}

.input-group {
	display: flex;
	align-items: center;
	background: white;
	border-radius: 8px;
	margin-bottom: 20px;
	padding: 0 15px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.input-icon {
	font-size: 20px;
	margin-right: 10px;
	color: #999;
}

.input-field {
	flex: 1;
	height: 50px;
	font-size: 16px;
	border: none;
	outline: none;
}

.get-code-btn {
	width: 100px;
	height: 35px;
	background: #52c41a;
	color: white;
	border: none;
	border-radius: 6px;
	font-size: 12px;
}

.get-code-btn:disabled {
	background: #ccc;
}

.register-section {
	margin-bottom: 30px;
}

.register-btn {
	width: 100%;
	height: 50px;
	background: #52c41a;
	color: white;
	border: none;
	border-radius: 8px;
	font-size: 18px;
	font-weight: bold;
	display: flex;
	align-items: center;
	justify-content: center;
	box-shadow: 0 4px 12px rgba(82, 196, 26, 0.3);
}

.countdown-text {
	margin-left: 10px;
	font-size: 14px;
	opacity: 0.8;
}

.footer-section {
	text-align: center;
}

.footer-text {
	color: #666;
	font-size: 14px;
	margin-right: 10px;
}

.login-link {
	color: #52c41a;
	font-size: 14px;
	text-decoration: underline;
}
</style>
