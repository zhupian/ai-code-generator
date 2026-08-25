# AI Code Generator Platform (ai-code-generator)

> Turn natural language requirements into code, and deploy the result as accessible pages with one click.

This project is an AI application generation platform built with **Spring Boot 3 + LangChain4j + Vue 3**. Users describe their requirements in natural language, and the AI automatically selects an appropriate generation mode (single-file HTML, multi-file static pages, or a Vue project), generates code files through tool calls, and streams the output in real time. Generated applications can be edited online, deployed and shared with one click, and downloaded as complete source code. A full-featured admin console is also included.

## ✨ Features

### 1. AI-Powered Code Generation
- Describe requirements in conversation; the AI analyzes them and picks the right generation strategy
- Generates code files via LangChain4j tool calling
- SSE streaming output to watch the AI work in real time

### 2. App Management
- Create, edit, and delete your own applications
- Paginated app lists, search, and featured-app showcase
- Chat history so you can return to previous conversations anytime

### 3. One-Click Deploy & Share
- Deploy generated applications to the cloud and get an accessible URL instantly
- Download the complete project source code
- Access deployed pages directly via a deploy key

### 4. Enterprise Admin Console
- User management, app management, and chat history management
- Admins can feature, unpublish, or delete applications

### 5. User System
- Register, log in, and log out (Redis session management with 30-day auto-login)

## 🛠 Tech Stack

### Backend
| Technology | Description |
|------|------|
| Spring Boot 3.5.4 | Application framework |
| LangChain4j 1.1.0 | AI model integration (DeepSeek, OpenAI-compatible protocol) |
| LangGraph4j | AI workflow orchestration |
| MyBatis-Flex | ORM persistence layer |
| MySQL | Business database |
| Redis | Session storage & caching |
| Knife4j | API documentation |
| Tencent Cloud COS | Object storage (deployment artifacts) |
| Selenium / WebDriverManager | Browser automation (page screenshots) |
| Caffeine | Local caching |
| Hutool | Utility library |

### Frontend
| Technology | Description |
|------|------|
| Vue 3 + TypeScript | Frontend framework |
| Vite | Build tool |
| ant-design-vue | UI component library |
| Pinia | State management |
| Vue Router | Routing |
| Axios | HTTP client |
| markdown-it / highlight.js | Chat content rendering |

## 🚀 Quick Start

### Prerequisites
- JDK 21+
- Maven 3.8+
- Node.js 18+ (for frontend build)
- MySQL 8+
- Redis 6+

### 1. Initialize the Database

Run `sql/create_table.sql` to initialize the database (default database name: `chat`):

```bash
mysql -u root -p < sql/create_table.sql
```

### 2. Configure the Backend

Edit `src/main/resources/application.yml`:

- **Datasource**: MySQL URL, username, and password
- **Redis**: host, port, and password
- **AI model**: set your DeepSeek API key in `langchain4j.open-ai.chat-model.api-key` (`base-url` defaults to `https://api.deepseek.com`)

> ⚠️ Never commit real API keys or database passwords to the repository.

### 3. Start the Backend

```bash
./mvnw spring-boot:run
```

The service runs at `http://localhost:8123/api` by default. API docs (Knife4j): `http://localhost:8123/api/doc.html`.

### 4. Start the Frontend

```bash
cd chatcode-frontend
npm install
npm run dev
```

The frontend runs at `http://localhost:5173` by default.

## 📁 Project Structure

```
ai-code-generator
├── src/main/java/com/zhuPian
│   ├── aicodegenerator/    # Core app-generation logic (AI, generator, LangGraph4j workflows)
│   └── chatcode/           # Platform business code (Controller, Service, Mapper, etc.)
├── src/main/resources/     # Config files, SQL mappings, AI prompts
├── chatcode-frontend/      # Vue 3 frontend
├── sql/create_table.sql    # Database initialization script
└── docs/                   # Project documentation
```

## 📄 API Documentation

After starting the backend, visit the Knife4j online docs at `http://localhost:8123/api/doc.html`.

## 🤝 Contributing

Contributions of any kind are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution workflow, branch naming, and commit conventions.

## 📜 License

This project is open-sourced under the [MIT License](LICENSE).
