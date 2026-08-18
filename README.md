# AI 代码生成平台（ai-code-generator）

> This is an AI application generation platform. After the user inputs their requirements, the system first selects a suitable generation mode for the application, and then uses LangChain4j to call the model to generate code. It supports three modes: single-file HTML, multi-file static pages, and Vue projects, and provides streaming generation and display, code storage, online preview, and deployment capabilities. The main focus of the project is to connect "natural language requirements -> code -> accessible pages," rather than just stopping at AI dialogue.

> 输入自然语言需求，AI 自动生成代码，并一键部署为可访问的页面。

本项目是一个基于 **Spring Boot 3 + LangChain4j + Vue 3** 的 AI 应用生成平台：用户用自然语言描述需求，AI 自动选择合适生成模式（单文件 HTML、多文件静态页、Vue 项目），通过工具调用生成代码文件，支持流式输出实时查看生成过程，生成的应用可在线编辑、一键部署分享、下载完整源码，并提供了完善的管理后台。

## ✨ 功能特性

### 1. AI 智能代码生成
- 对话式描述需求，AI 自动分析并选择合适的生成策略
- 基于 LangChain4j 工具调用生成代码文件
- SSE 流式输出，实时看到 AI 的执行过程

### 2. 应用管理
- 创建、编辑、删除自己的应用
- 应用分页列表、搜索查询、精选应用展示
- 聊天历史记录，随时回到之前的对话

### 3. 一键部署分享
- 生成的应用一键部署到云端，自动获得可访问地址
- 支持下载完整项目源码
- 通过 deployKey 直接访问已部署的页面

### 4. 企业级管理后台
- 用户管理、应用管理、聊天记录管理
- 管理员可对应用进行精选、下架、删除等操作

### 5. 用户体系
- 注册、登录、登出（Redis Session 会话管理，30 天免登录）

## 🛠 技术栈

### 后端
| 技术 | 说明 |
|------|------|
| Spring Boot 3.5.4 | 应用框架 |
| LangChain4j 1.1.0 | AI 模型接入（DeepSeek，OpenAI 兼容协议） |
| LangGraph4j | AI 工作流编排 |
| MyBatis-Flex | ORM 持久层 |
| MySQL | 业务数据库 |
| Redis | Session 存储与缓存 |
| Knife4j | 接口文档 |
| 腾讯云 COS | 对象存储（部署产物） |
| Selenium / WebDriverManager | 浏览器自动化（页面截图） |
| Caffeine | 本地缓存 |
| Hutool | 工具库 |

### 前端
| 技术 | 说明 |
|------|------|
| Vue 3 + TypeScript | 前端框架 |
| Vite | 构建工具 |
| ant-design-vue | UI 组件库 |
| Pinia | 状态管理 |
| Vue Router | 路由 |
| Axios | HTTP 请求 |
| markdown-it / highlight.js | 聊天内容渲染 |

## 🚀 快速开始

### 环境要求
- JDK 21+
- Maven 3.8+
- Node.js 18+（前端构建）
- MySQL 8+
- Redis 6+

### 1. 初始化数据库

执行 `sql/create_table.sql` 初始化数据库（默认数据库名 `chat`）：

```bash
mysql -u root -p < sql/create_table.sql
```

### 2. 配置后端

修改 `src/main/resources/application.yml`：

- **数据源**：MySQL 连接地址、用户名、密码
- **Redis**：连接地址、端口、密码
- **AI 模型**：`langchain4j.open-ai.chat-model.api-key` 填入你的 DeepSeek API Key，`base-url` 默认指向 `https://api.deepseek.com`

> ⚠️ 请勿将真实的 API Key 和数据库密码提交到仓库。

### 3. 启动后端

```bash
./mvnw spring-boot:run
```

服务默认运行在 `http://localhost:8123/api`，接口文档地址：`http://localhost:8123/api/doc.html`（Knife4j）。

### 4. 启动前端

```bash
cd chatcode-frontend
npm install
npm run dev
```

前端默认运行在 `http://localhost:5173`。

## 📁 目录结构

```
ai-code-generator
├── src/main/java/com/zhuPian
│   ├── aicodegenerator/    # 应用生成核心逻辑（AI、生成器、LangGraph4j 工作流）
│   └── chatcode/           # 平台业务代码（Controller、Service、Mapper 等）
├── src/main/resources/     # 配置文件、SQL 映射、AI 提示词
├── chatcode-frontend/      # Vue 3 前端
├── sql/create_table.sql    # 数据库初始化脚本
└── docs/                   # 项目文档
```

## 📄 接口文档

启动后端后访问 Knife4j 在线文档：`http://localhost:8123/api/doc.html`

## 🤝 贡献指南

欢迎任何形式的贡献！请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解贡献流程、分支与提交规范。

## 📜 License

本项目基于 [MIT License](LICENSE) 开源。
