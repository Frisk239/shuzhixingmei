<template>
	<view class="tools-container">
		<!-- AI病果识别区 -->
		<view class="ai-recognition-section">
			<view class="ai-header">
				<text class="ai-title">AI病果识别</text>
				<text class="ai-subtitle">拍照按钮点击</text>
				<text class="ai-desc">图片上传加载+病果分类结果</text>
				<text class="ai-desc">弹窗</text>
			</view>

			<view class="camera-section">
				<view class="camera-circle">
					<view class="camera-icon">📷</view>
					<text class="camera-text">拍照识别</text>
				</view>

				<view class="history-section">
					<view class="history-icon">🕐</view>
					<text class="history-text">历史记录</text>
				</view>

				<view class="help-section">
					<view class="help-icon">❓</view>
					<text class="help-text">识别指南</text>
				</view>
			</view>
		</view>

		<!-- 数据查询区 -->
		<view class="data-section">
			<view class="data-label">数据查询：</view>
			<view class="data-options">
				<view :class="['data-option', { active: selectedDataType === 'soil' }]" @click="selectDataType('soil')">
					<text class="option-text">土壤墒情</text>
				</view>
				<view :class="['data-option', { active: selectedDataType === 'price' }]" @click="selectDataType('price')">
					<text class="option-text">收购价</text>
				</view>
			</view>
		</view>

		<!-- 区域筛选 -->
		<view class="region-filter">
			<text class="filter-label">区域筛选</text>
			<picker :range="regions" @change="onRegionChange">
				<view class="picker-display">
					<text>{{ selectedRegion }}</text>
					<text class="arrow">▼</text>
				</view>
			</picker>
			<view class="refresh-btn" @click="refreshData">
				<text class="refresh-icon">🔄</text>
				<text class="refresh-text">刷新</text>
			</view>
		</view>

		<!-- 数据展示区 -->
		<view class="data-display">
			<view class="data-item" v-for="item in currentData" :key="item.id">
				<view class="data-icon">{{ item.icon }}</view>
				<view class="data-info">
					<text class="data-title">{{ item.title }}</text>
					<text class="data-value">{{ item.value }}</text>
				</view>
			</view>
		</view>

		<!-- 分割线 -->
		<view class="divider">
			<text class="divider-text">上中下</text>
		</view>

		<!-- 视频播放区 -->
		<view class="video-section">
			<view class="video-container">
				<video
					id="videoPlayer"
					src="/static/video.mp4"
					class="video-player"
					controls="true"
					poster="/static/logo.png"
					autoplay="false"
					loop="false"
					muted="false"
					show-progress="true"
					show-fullscreen-btn="true"
					show-play-btn="true"
					show-center-play-btn="true"
					enable-progress-gesture="true"
					object-fit="contain"
				></video>
				<text class="video-title">永泰矮化青梅1号</text>
			</view>
		</view>

		<!-- 品种介绍 -->
		<view class="variety-info">
			<view class="info-item">
				<text class="check-icon">✅</text>
				<text class="info-text">优势苗田，规范时优势</text>
			</view>
			<view class="info-item">
				<text class="check-icon">✅</text>
				<text class="info-text">青泰梅标准，是选的优势</text>
			</view>
		</view>

		<!-- 操作按钮 -->
		<view class="action-buttons">
			<button class="action-btn buy-btn" @click="buySeedlings">
				<text class="btn-text">购买苗木</text>
			</button>
			<button class="action-btn consult-btn" @click="technicalConsult">
				<text class="btn-text">技术咨询</text>
			</button>
		</view>
	</view>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

// 数据类型
const selectedDataType = ref('soil')
const selectedRegion = ref('永泰县')

// 区域选项
const regions = ref(['永泰县', '福州市', '莆田市', '泉州市'])

// 土壤墒情数据
const soilData = ref([
	{ id: 1, icon: '💧', title: '桔柯镇', value: '2Y' },
	{ id: 2, icon: '☀️', title: '土壤湿度', value: '28%' },
	{ id: 3, icon: '🌡️', title: '土壤温度', value: '23°C' }
])

// 收购价数据
const priceData = ref([
	{ id: 1, icon: '💰', title: '当前价格', value: '¥15.8/kg' },
	{ id: 2, icon: '📈', title: '价格趋势', value: '上涨' },
	{ id: 3, icon: '📊', title: '交易量', value: '1200kg' }
])

// 当前显示的数据
const currentData = computed(() => {
	return selectedDataType.value === 'soil' ? soilData.value : priceData.value
})

// 选择数据类型
const selectDataType = (type: string) => {
	selectedDataType.value = type
}

// 区域选择
const onRegionChange = (e: any) => {
	selectedRegion.value = regions.value[e.detail.value]
}

// 刷新数据
const refreshData = () => {
	uni.showToast({
		title: '数据已刷新',
		icon: 'success'
	})
}

// 拍照识别
const takePhoto = () => {
	uni.chooseImage({
		count: 1,
		sizeType: ['original', 'compressed'],
		sourceType: ['camera'],
		success: (res) => {
			// 模拟分析结果
			setTimeout(() => {
				uni.showModal({
					title: '分析结果',
					content: '检测到炭疽病，建议使用针对性药剂进行防治',
					showCancel: false,
					confirmText: '我知道了'
				})
			}, 2000)
		}
	})
}

// 购买苗木
const buySeedlings = () => {
	uni.showToast({
		title: '跳转到购买页面',
		icon: 'success'
	})
}

// 技术咨询
const technicalConsult = () => {
	uni.showToast({
		title: '联系技术专家',
		icon: 'success'
	})
}
</script>

<style scoped>
.tools-container {
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

.ai-recognition-section {
	margin: 0px 20px 20px;
	background: white;
	border-radius: 12px;
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.ai-header {
	text-align: center;
	margin-bottom: 20px;
}

.ai-title {
	display: block;
	font-size: 20px;
	font-weight: bold;
	color: #333;
	margin-bottom: 8px;
}

.ai-subtitle {
	display: block;
	font-size: 16px;
	color: #666;
	margin-bottom: 4px;
}

.ai-desc {
	display: block;
	font-size: 14px;
	color: #999;
}

.camera-section {
	display: flex;
	justify-content: space-around;
	align-items: center;
}

.camera-circle {
	width: 80px;
	height: 80px;
	border: 3px solid #52c41a;
	border-radius: 50%;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	cursor: pointer;
	transition: transform 0.2s;
}

.camera-circle:active {
	transform: scale(0.9);
}

.camera-icon {
	font-size: 24px;
	margin-bottom: 4px;
}

.camera-text {
	font-size: 12px;
	color: #52c41a;
}

.history-section, .help-section {
	text-align: center;
	cursor: pointer;
}

.history-icon, .help-icon {
	font-size: 24px;
	margin-bottom: 4px;
}

.history-text, .help-text {
	font-size: 12px;
	color: #666;
}

.data-section {
	margin: 20px;
	background: white;
	border-radius: 12px;
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.data-label {
	font-size: 16px;
	font-weight: bold;
	color: #333;
	margin-bottom: 15px;
}

.data-options {
	display: flex;
	gap: 20px;
}

.data-option {
	padding: 8px 16px;
	border-radius: 20px;
	cursor: pointer;
	transition: all 0.2s;
}

.data-option.active {
	background: #52c41a;
	color: white;
}

.data-option .option-text {
	font-size: 14px;
}

.region-filter {
	margin: 20px;
	background: white;
	border-radius: 12px;
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.filter-label {
	font-size: 16px;
	color: #333;
}

.picker-display {
	display: flex;
	align-items: center;
	cursor: pointer;
}

.picker-display text {
	font-size: 14px;
	color: #666;
}

.arrow {
	font-size: 12px;
	color: #999;
	margin-left: 8px;
}

.refresh-btn {
	display: flex;
	align-items: center;
	cursor: pointer;
}

.refresh-icon {
	font-size: 16px;
	margin-right: 4px;
}

.refresh-text {
	font-size: 14px;
	color: #666;
}

.data-display {
	margin: 20px;
	display: flex;
	flex-direction: column;
	gap: 15px;
}

.data-item {
	background: white;
	border-radius: 12px;
	padding: 20px;
	display: flex;
	align-items: center;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.data-icon {
	font-size: 24px;
	margin-right: 15px;
}

.data-info {
	flex: 1;
}

.data-title {
	display: block;
	font-size: 14px;
	color: #666;
	margin-bottom: 4px;
}

.data-value {
	display: block;
	font-size: 18px;
	font-weight: bold;
	color: #333;
}

.divider {
	text-align: center;
	margin: 30px 20px;
	position: relative;
}

.divider::before {
	content: '';
	position: absolute;
	top: 50%;
	left: 0;
	right: 0;
	height: 1px;
	background: #e0e0e0;
}

.divider-text {
	background: #f6ffed;
	padding: 0 20px;
	color: #999;
	font-size: 14px;
	position: relative;
	z-index: 1;
}

.video-section {
	margin: 20px;
}

.video-container {
	background: white;
	border-radius: 12px;
	overflow: hidden;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
	position: relative;
}

.video-player {
	width: 100%;
	height: 200px;
	border-radius: 12px;
}

.video-title {
	position: absolute;
	bottom: 0;
	left: 0;
	right: 0;
	background: linear-gradient(transparent, rgba(0, 0, 0, 0.7));
	color: white;
	padding: 20px 15px 15px;
	font-size: 16px;
	font-weight: bold;
	pointer-events: none;
}

.variety-info {
	margin: 20px;
	background: white;
	border-radius: 12px;
	padding: 20px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.info-item {
	display: flex;
	align-items: center;
	margin-bottom: 15px;
}

.info-item:last-child {
	margin-bottom: 0;
}

.check-icon {
	font-size: 18px;
	margin-right: 10px;
	color: #52c41a;
}

.info-text {
	font-size: 14px;
	color: #333;
}

.action-buttons {
	margin: 30px 20px 20px;
	display: flex;
	gap: 15px;
}

.action-btn {
	flex: 1;
	height: 50px;
	border: none;
	border-radius: 8px;
	font-size: 16px;
	font-weight: bold;
	cursor: pointer;
}

.buy-btn {
	background: #ff7a45;
	color: white;
}

.consult-btn {
	background: #ffc069;
	color: white;
}
</style>
