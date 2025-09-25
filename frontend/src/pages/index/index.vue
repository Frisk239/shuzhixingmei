<template>
	<view class="home-container">
		<!-- 轮播图区域 -->
		<view class="carousel-section">
			<swiper class="carousel" indicator-dots="true" autoplay="true" interval="3000" circular="true">
				<swiper-item v-for="(item, index) in carouselImages" :key="index">
					<view class="carousel-item">
						<image
							:src="item.src"
							class="carousel-image"
							mode="aspectFill"
							@click="previewImage(item.src)"
						/>
					</view>
				</swiper-item>
			</swiper>
		</view>

		<!-- AI病果识别区 -->
		<view class="ai-section">
			<view class="ai-box">
				<text class="ai-title">AI病果识别区</text>
				<text class="ai-subtitle">智能识别青梅病害，提供防治建议</text>
			</view>
		</view>

		<!-- 功能导航区 -->
		<view class="features-section">
			<view class="feature-item" @click="goToTools">
				<view class="feature-icon">🔧</view>
				<text class="feature-text">产业工具</text>
			</view>
			<view class="feature-item" @click="goToCooperation">
				<view class="feature-icon">🤝</view>
				<text class="feature-text">校企农协同</text>
			</view>
			<view class="feature-item" @click="goToAbout">
				<view class="feature-icon">ℹ️</view>
				<text class="feature-text">关于我们</text>
			</view>
		</view>


	</view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 轮播图数据（暂时使用占位符）
const carouselImages = ref([
	{ src: '/static/logo.png' },
	{ src: '/static/logo.png' },
	{ src: '/static/logo.png' }
])

// 预览图片
const previewImage = (src: string) => {
	uni.previewImage({
		current: src,
		urls: carouselImages.value.map(item => item.src)
	})
}

// 跳转到产业工具页面
const goToTools = () => {
	uni.navigateTo({
		url: '/pages/tools/tools'
	})
}

// 跳转到校企农协同页面
const goToCooperation = () => {
	uni.navigateTo({
		url: '/pages/cooperation/cooperation'
	})
}

// 跳转到关于我们页面
const goToAbout = () => {
	uni.navigateTo({
		url: '/pages/about/about'
	})
}

// 跳转到登录页面
const goToLogin = () => {
	uni.navigateTo({
		url: '/pages/login/login'
	})
}

// 切换到首页
const switchToHome = () => {
	uni.navigateTo({
		url: '/pages/index/index'
	})
}
</script>

<style scoped>
.home-container {
	min-height: 750px;
	background: linear-gradient(135deg, #f6ffed 0%, #d9f7be 100%);
	padding-bottom: 20px;
}

.header-section {
	padding: 40px 20px 20px;
	text-align: center;
}

.main-title {
	font-size: 28px;
	font-weight: bold;
	color: #333;
}

.carousel-section {
	margin: 0px 20px 20px;
	border-radius: 12px;
	overflow: hidden;
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.carousel {
	height: 220px;
}

.carousel-item {
	height: 100%;
}

.carousel-image {
	width: 100%;
	height: 100%;
}

.ai-section {
	margin: 40px 20px;
}

.ai-box {
	background: linear-gradient(135deg, #52c41a 0%, #389e0d 100%);
	border-radius: 12px;
	padding: 35px 20px;
	text-align: center;
	box-shadow: 0 4px 12px rgba(82, 196, 26, 0.3);
}

.ai-title {
	display: block;
	font-size: 26px;
	font-weight: bold;
	color: white;
	margin-bottom: 12px;
}

.ai-subtitle {
	display: block;
	font-size: 15px;
	color: rgba(255, 255, 255, 0.9);
}

.features-section {
	display: flex;
	justify-content: space-around;
	margin: 50px 20px 40px;
}

.feature-item {
	background: white;
	border-radius: 12px;
	padding: 20px 15px;
	text-align: center;
	width: 30%;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
	transition: transform 0.2s;
}

.feature-item:active {
	transform: scale(0.95);
}

.feature-icon {
	font-size: 30px;
	margin-bottom: 10px;
}

.feature-text {
	font-size: 14px;
	color: #333;
	font-weight: 500;
}

.bottom-nav {
	position: fixed;
	bottom: 0;
	left: 0;
	right: 0;
	background: white;
	display: flex;
	border-top: 1px solid #e0e0e0;
}

.nav-item {
	flex: 1;
	padding: 12px;
	text-align: center;
	transition: background-color 0.2s;
}

.nav-item.active {
	background: #52c41a;
}

.nav-item.active .nav-text {
	color: white;
}

.nav-icon {
	font-size: 20px;
	margin-bottom: 4px;
}

.nav-text {
	font-size: 12px;
	color: #666;
}

.nav-item.active .nav-icon {
	color: white;
}
</style>
