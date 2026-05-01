# IdeaProjects

一个基于 Spring Boot + Vue 3 的前后端分离项目。

## 项目结构

```
├── demo/                 # Spring Boot 后端项目
│   ├── src/
│   ├── pom.xml
│   └── ...
├── vue-demo/             # Vue 3 前端项目
│   ├── src/
│   ├── package.json
│   └── ...
└── README.md
```

## 技术栈

### 后端 (demo)

- **框架**: Spring Boot 4.0.5
- **ORM**: MyBatis 4.0.1
- **数据库**: MySQL
- **Java 版本**: 17
- **其他依赖**:
  - Lombok - 简化代码
  - Spring Boot DevTools - 开发热部署
  - MySQL Connector - 数据库驱动

### 前端 (vue-demo)

- **框架**: Vue 3.5.31
- **构建工具**: Vite 8.0.3
- **路由**: Vue Router 5.0.4
- **状态管理**: Pinia 3.0.4
- **HTTP 客户端**: Axios 1.14.0
- **代码检查**: ESLint + Oxlint

## 快速开始

### 环境要求

- Node.js ^20.19.0 || >=22.12.0
- Java 17
- Maven
- MySQL 5.7+

### 后端启动

1. 进入后端目录：
   ```sh
   cd demo
   ```

2. 配置数据库：
   - 创建 MySQL 数据库 `localhost`
   - 修改 `src/main/resources/application.properties` 中的数据库配置

3. 启动后端：
   ```sh
   # Windows
   mvnw.cmd spring-boot:run
   
   # Linux/Mac
   ./mvnw spring-boot:run
   ```

   或者直接运行：
   ```sh
   mvn spring-boot:run
   ```

4. 后端服务将运行在 `http://localhost:8081`

### 前端启动

1. 进入前端目录：
   ```sh
   cd vue-demo
   ```

2. 安装依赖：
   ```sh
   npm install
   ```

3. 启动开发服务器：
   ```sh
   npm run dev
   ```

4. 前端服务将运行在 `http://localhost:5173`（默认端口）

## API 接口

### 测试接口

```
GET /api/test
```

响应：`"成功！！！"`

### 登录接口

```
POST /api/login
```

请求体：
```json
{
  "username": "admin",
  "password": "123456"
}
```

响应示例（成功）：
```json
{
  "code": 200,
  "msg": "登录成功！",
  "token": "your_token_123456"
}
```

响应示例（失败）：
```json
{
  "code": 401,
  "msg": "账号或密码错误！"
}
```

## 配置说明

### 后端配置

配置文件位于 `demo/src/main/resources/application.properties`：

```properties
server.port=8081

spring.datasource.url=jdbc:mysql://localhost:3306/localhost?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```

### 跨域配置

后端已配置 CORS，允许前端跨域访问：
- 允许所有接口跨域
- 允许所有请求方式
- 支持携带 cookie

## 开发指南

### 代码规范

- 前端使用 ESLint + Oxlint 进行代码检查
- 运行 `npm run lint` 检查并修复代码问题

### 构建生产版本

```sh
# 前端构建
cd vue-demo
npm run build

# 后端构建
cd demo
mvnw.cmd package
```

## 注意事项

1. 确保 MySQL 服务已启动
2. 测试账号：`admin` / `123456`
3. 前后端分离开发，后端已配置跨域支持
