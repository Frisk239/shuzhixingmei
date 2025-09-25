<template>
	<view class="about-container">
		<!-- 项目起源 -->
		<view class="section">
			<view class="section-title">项目起源</view>
			<view class="section-content">
				<text class="content-text">
					永泰青梅产业服务平台致力于为青梅种植户提供全方位的数字化服务，
					通过AI技术赋能传统农业，提升产业效率。
				</text>
			</view>
		</view>

		<!-- 问题描述 -->
		<view class="section">
			<view class="section-title">解决的问题</view>
			<view class="problem-box">
				<text class="problem-text">高树摘果损耗大 分拣效率低</text>
				<text class="solution-text">
					通过矮化品种推广和智能化管理，降低采摘损耗，提高分拣效率。
				</text>
			</view>
		</view>

		<!-- 团队与资质 -->
		<view class="section">
			<view class="section-title">团队与资质</view>
			<view class="team-section">
				<view class="team-item">
					<view class="team-icon">👥</view>
					<text class="team-text">专业技术团队</text>
				</view>
				<view class="team-item">
					<view class="team-icon">🏆</view>
					<text class="team-text">农业科技资质</text>
				</view>
				<view class="team-item">
					<view class="team-icon">🔬</view>
					<text class="team-text">科研合作单位</text>
				</view>
			</view>
		</view>

		<!-- 联系方式 -->
		<view class="section">
			<view class="section-title">联系我们</view>
			<view class="contact-section">
				<view class="contact-item">
					<view class="contact-icon">📞</view>
					<text class="contact-text">电话：400-123-4567</text>
				</view>
				<view class="contact-item">
					<view class="contact-icon">📧</view>
					<text class="contact-text">邮箱：info@qmgzy.com</text>
				</view>
				<view class="contact-item">
					<view class="contact-icon">📍</view>
					<text class="contact-text">地址：福建省福州市永泰县</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup lang="ts">
// 跳转到首页
const goToHome = () => {
	uni.navigateTo({
		url: '/pages/index/index'
	})
}

// 跳转到关于我们页面（当前页面）
const goToAbout = () => {
	// 已经在当前页面，无需跳转
}
</script>

<style scoped>
.about-container {
	min-height: 750px;
	background: linear-gradient(135deg, #f6ffed 0%, #d9f7be 100%);
	padding-bottom: 20px;
}

.header-section {
	padding: 40px 20px 20px;
	text-align: center;
}

.page-title {
	font-size: 28px;
	font-weight: bold;
	color: #333;
}

.section {
	margin: 0px 20px 20px;
	background: white;
	border-radius: 12px;
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.section-title {
	font-size: 18px;
	font-weight: bold;
	color: #52c41a;
	margin-bottom: 15px;
}

.content-text {
	font-size: 14px;
	color: #666;
	line-height: 1.6;
}

.problem-box {
	background: linear-gradient(135deg, #fff2f0 0%, #ffccc7 100%);
	border-radius: 8px;
	padding: 15px;
	margin-top: 10px;
}

.problem-text {
	display: block;
	font-size: 16px;
	font-weight: bold;
	color: #cf1322;
	margin-bottom: 10px;
}

.solution-text {
	display: block;
	font-size: 14px;
	color: #666;
	line-height: 1.5;
}

.team-section {
	display: flex;
	justify-content: space-around;
	flex-wrap: wrap;
}

.team-item {
	text-align: center;
	width: 30%;
	margin-bottom: 15px;
}

.team-icon {
	font-size: 30px;
	margin-bottom: 8px;
}

.team-text {
	font-size: 12px;
	color: #666;
}

.contact-section {
	display: flex;
	flex-direction: column;
	gap: 15px;
}

.contact-item {
	display: flex;
	align-items: center;
	padding: 10px 0;
	border-bottom: 1px solid #f0f0f0;
}

.contact-item:last-child {
	border-bottom: none;
}

.contact-icon {
	font-size: 20px;
	margin-right: 15px;
	min-width: 20px;
}

.contact-text {
	font-size: 14px;
	color: #333;
}

/* 底部导航栏样式 */
.bottom-nav {
	position: fixed;
	bottom: 0;
	left: 0;
	right: 0;
	background: white;
	display: flex;
	border-top: 1px solid #e0e0e0;
	padding-bottom: env(safe-area-inset-bottom);
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
