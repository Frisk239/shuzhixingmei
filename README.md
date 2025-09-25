# 永泰青梅产业服务

一个基于uniapp + Vue3 + TypeScript的前端应用和Spring Boot后端的移动端服务平台。

## 项目结构

```
shuzhixingmei/
├── frontend/          # uniapp前端项目
│   ├── src/
│   │   ├── pages/     # 页面文件
│   │   ├── static/    # 静态资源
│   │   └── types/     # TypeScript类型定义
│   └── package.json
├── backend/           # Spring Boot后端项目
│   ├── src/
│   │   ├── main/java/com/shuzhixingmei/
│   │   └── main/resources/
│   └── pom.xml
└── README.md
```

## 功能特性

### 前端功能
- ✅ 注册登录页面
- ✅ 首页：轮播图展示、AI病果识别展示、功能板块导航
- ✅ 产业工具页面：AI病果识别、土壤墒情数据、收购价数据、视频播放模块
- ✅ 校企农协同页面：品种推广轮播、农户提问区、企业合作意向墙
- ✅ 关于我们页面：项目起源、团队资质、联系方式
- ✅ 手机边框调试样式（H5模式）

### 后端功能
- ✅ 用户注册登录API
- ✅ 土壤墒情数据API
- ✅ 收购价数据API
- ✅ 图片上传和AI诊断API（模拟）
- ✅ H2内存数据库

## 运行环境要求

- Node.js 16+
- Java 17+
- Maven 3.6+

## 安装和运行

### 前端运行

1. 进入前端目录：
```bash
cd frontend
```

2. 安装依赖：
```bash
npm install
```

3. 运行H5开发模式（带手机边框）：
```bash
npm run dev:h5
```

前端将在浏览器中运行，显示带有手机边框的移动端界面。

### 后端运行

1. 确保Java已安装（项目使用Maven Wrapper，无需单独安装Maven）：
```bash
java -version
```

2. 进入后端目录：
```bash
cd backend
```

3. 运行Spring Boot应用：
```bash
# Windows
./mvnw.cmd spring-boot:run

# Linux/Mac
./mvnw spring-boot:run
```

**注意**：首次运行时，Maven Wrapper会自动下载Maven，无需手动安装。

后端将在 http://localhost:8080 启动。

### API接口

- POST `/api/auth/login` - 用户登录
- POST `/api/auth/register` - 用户注册
- GET `/api/data/soil-moisture` - 获取土壤墒情数据
- GET `/api/data/price` - 获取收购价数据
- POST `/api/data/upload-image` - 上传图片进行AI诊断

### H2数据库控制台

访问 http://localhost:8080/h2-console 进入数据库控制台。

连接信息：
- JDBC URL: `jdbc:h2:mem:shuzhixingmei`
- Username: `sa`
- Password: (空)

## 开发说明

### 前端技术栈
- uniapp框架
- Vue 3 + TypeScript
- 绿色主题设计
- 响应式布局

### 后端技术栈
- Spring Boot 3.1.0
- Spring Data JPA
- H2数据库
- RESTful API

## 部署说明

### 前端部署
```bash
# 构建H5版本
npm run build:h5

# 构建微信小程序版本
npm run build:mp-weixin
```

### 后端部署
```bash
# 打包
mvn clean package

# 运行jar包
java -jar target/backend-0.0.1-SNAPSHOT.jar
```

## 注意事项

1. 当前后端使用H2内存数据库，重启后数据会丢失
2. AI诊断功能为模拟实现，返回固定结果
3. 前端H5模式会显示手机边框样式，方便调试
4. 图片资源已包含在static目录中

## 后续扩展

- [ ] 集成真实AI模型进行病果识别
- [ ] 替换H2为MySQL等持久化数据库
- [ ] 添加用户权限管理
- [ ] 实现实时数据推送
- [ ] 添加更多数据可视化图表
