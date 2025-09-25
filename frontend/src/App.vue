<script>
export default {
  onLaunch: function () {
    console.log('App Launch')
  },
  onShow: function () {
    console.log('App Show')
  },
  onHide: function () {
    console.log('App Hide')
  },
}
</script>

<style>
/* 移动端模拟器容器样式 */
#app {
  width: 350px;
  height: 750px; /* 9:19.5比例，350 * 19.5 / 9 ≈ 761，稍微缩小到750 */
  margin: 20px auto;
  border: 2px solid #e0e0e0;
  border-radius: 20px;
  overflow: auto; /* 允许内部滚动 */
  position: relative;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
}

/* 隐藏容器滚动条 */
#app::-webkit-scrollbar {
  display: none;
}

#app {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

/* 电脑端居中显示 */
@media (min-width: 768px) {
  #app {
    margin: 20px auto;
  }
}

/* 移动端全屏显示 */
@media (max-width: 767px) {
  #app {
    width: 100vw;
    height: 100vh;
    margin: 0;
    border: none;
    border-radius: 0;
    box-shadow: none;
  }
}

/* 页面容器样式 */
.uni-page-body {
  height: 100%;
  overflow: hidden;
}

/* 确保所有页面内容都在容器内 */
.uni-page-wrapper {
  height: 100%;
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  padding-top: 0 !important;
}

/* 移除页面默认的顶部间距 */
.uni-page-head {
  display: none !important;
}

.uni-page-body {
  padding-top: 0 !important;
}

/* 自定义滚动条样式 */
.uni-page-wrapper::-webkit-scrollbar {
  width: 6px;
}

.uni-page-wrapper::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.1);
  border-radius: 3px;
}

.uni-page-wrapper::-webkit-scrollbar-thumb {
  background: rgba(82, 196, 26, 0.5);
  border-radius: 3px;
}

.uni-page-wrapper::-webkit-scrollbar-thumb:hover {
  background: rgba(82, 196, 26, 0.7);
}
</style>
