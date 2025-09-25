<template>
	<view class="cooperation-container">
		<!-- 轮播图区域 -->
		<view class="carousel-section">
			<swiper class="carousel" indicator-dots="true" autoplay="true" interval="3000" circular="true">
				<swiper-item v-for="(item, index) in carouselImages" :key="index">
					<view class="carousel-item">
						<image :src="item.src" class="carousel-image" mode="aspectFill" />
					</view>
				</swiper-item>
			</swiper>
		</view>

		<!-- 矮化品种推广标题 -->
		<view class="promotion-title">
			<text class="title-text">矮化品种推广</text>
		</view>

		<!-- 品种展示区域 -->
		<view class="variety-showcase">
			<view class="showcase-item" v-for="item in varietyItems" :key="item.id">
				<image :src="item.image" class="showcase-image" mode="aspectFill" />
				<view class="showcase-info">
					<text class="showcase-title">{{ item.title }}</text>
					<text class="showcase-desc">{{ item.description }}</text>
				</view>
			</view>
		</view>

		<!-- 轮播图标题 -->
		<view class="section-title">
			<text class="title-text">矮化品种试验田丰收</text>
		</view>

		<!-- 丰收展示轮播 -->
		<view class="harvest-carousel">
			<swiper class="harvest-swiper" indicator-dots="true" autoplay="true" interval="4000" circular="true">
				<swiper-item v-for="(item, index) in harvestImages" :key="index">
					<view class="harvest-item">
						<image :src="item.src" class="harvest-image" mode="aspectFill" />
					</view>
				</swiper-item>
			</swiper>
		</view>

		<!-- 功能区域 -->
		<view class="features-section">
			<view class="feature-card question-card" @click="showQuestionModal">
				<view class="card-icon">❓</view>
				<text class="card-title">农户提问区</text>
				<button class="card-btn" @click.stop="askQuestion">我要提问</button>
			</view>

			<view class="feature-card cooperation-card" @click="showCooperationModal">
				<view class="card-icon">🤝</view>
				<text class="card-title">企业合作意向墙</text>
				<button class="card-btn" @click.stop="publishDemand">发布需求</button>
			</view>
		</view>
	</view>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 轮播图数据
const carouselImages = ref([
	{ src: '/static/logo.png' },
	{ src: '/static/logo.png' },
	{ src: '/static/logo.png' }
])

// 品种展示数据
const varietyItems = ref([
	{
		id: 1,
		image: '/static/logo.png',
		title: '矮化品种试验田标收',
		description: '覆盖面积：4.6亩'
	},
	{
		id: 2,
		image: '/static/logo.png',
		title: '优质青梅品种展示',
		description: '种植周期：3年'
	},
	{
		id: 3,
		image: '/static/logo.png',
		title: '智能化管理示范',
		description: '产量提升：25%'
	}
])

// 丰收展示数据
const harvestImages = ref([
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

// 显示问题弹窗
const showQuestionModal = () => {
	uni.showToast({
		title: '打开农户提问区',
		icon: 'success'
	})
}

// 提问
const askQuestion = () => {
	uni.showToast({
		title: '跳转到提问页面',
		icon: 'success'
	})
}

// 显示合作弹窗
const showCooperationModal = () => {
	uni.showToast({
		title: '打开企业合作意向墙',
		icon: 'success'
	})
}

// 发布需求
const publishDemand = () => {
	uni.showToast({
		title: '跳转到发布需求页面',
		icon: 'success'
	})
}
</script>

<style scoped>
.cooperation-container {
	min-height: 750px;
	background: linear-gradient(135deg, #f6ffed 0%, #d9f7be 100%);
	padding-bottom: 20px;
}

.header-section {
	padding: 40px 20px 20px;
	text-align: center;
}

.main-title {
	font-size: 24px;
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
	height: 200px;
}

.carousel-item {
	height: 100%;
}

.carousel-image {
	width: 100%;
	height: 100%;
}

.promotion-title {
	text-align: center;
	margin: 30px 20px 20px;
}

.title-text {
	font-size: 20px;
	font-weight: bold;
	color: #333;
}

.variety-showcase {
	display: flex;
	justify-content: space-around;
	margin: 20px;
}

.showcase-item {
	background: white;
	border-radius: 12px;
	padding: 15px;
	width: 30%;
	text-align: center;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.showcase-image {
	width: 100%;
	height: 80px;
	border-radius: 8px;
	margin-bottom: 10px;
}

.showcase-title {
	font-size: 12px;
	font-weight: bold;
	color: #333;
	margin-bottom: 5px;
}

.showcase-desc {
	font-size: 10px;
	color: #666;
	text-align: center;
	display: block;
	margin-top: 5px;
}

.section-title {
	text-align: center;
	margin: 30px 20px 20px;
}

.harvest-carousel {
	margin: 20px;
	border-radius: 12px;
	overflow: hidden;
	box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.harvest-swiper {
	height: 200px;
}

.harvest-item {
	height: 100%;
}

.harvest-image {
	width: 100%;
	height: 100%;
}

.features-section {
	display: flex;
	justify-content: space-around;
	margin: 30px 20px;
}

.feature-card {
	background: white;
	border-radius: 12px;
	padding: 20px;
	width: 45%;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
	text-align: center;
}

.card-icon {
	font-size: 30px;
	margin-bottom: 10px;
}

.card-title {
	font-size: 16px;
	font-weight: bold;
	color: #333;
	margin-bottom: 15px;
}

.card-btn {
	background: #52c41a;
	color: white;
	border: none;
	border-radius: 6px;
	padding: 8px 16px;
	font-size: 12px;
}

.bottom-info {
	text-align: center;
	margin: 40px 20px 20px;
}

.info-text {
	font-size: 14px;
	color: #666;
}
</style>
