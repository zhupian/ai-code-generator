# 贡献指南

感谢你愿意为 **AI 代码生成平台** 贡献代码！无论是修复 bug、新增功能、完善文档、补充测试，还是优化示例，都非常欢迎。

## 目录

- [开发环境](#开发环境)
- [贡献流程](#贡献流程)
- [分支命名规范](#分支命名规范)
- [提交信息规范](#提交信息规范)
- [Pull Request 要求](#pull-request-要求)
- [代码风格](#代码风格)

## 开发环境

- JDK 21+
- Maven 3.8+
- Node.js 18+
- MySQL 8+、Redis 6+

## 贡献流程

1. **Fork 本仓库**，将代码克隆到本地：

   ```bash
   git clone https://github.com/<你的用户名>/ai-code-generator.git
   cd ai-code-generator
   git remote add upstream https://github.com/zhupian/ai-code-generator.git
   ```

2. **同步最新代码**（每次动手前都执行一次，避免冲突）：

   ```bash
   git fetch upstream
   git checkout master
   git merge upstream/master
   ```

3. **创建功能分支**（见下方命名规范），在分支上完成修改。

4. **本地验证**：
   - 后端：`./mvnw -q compile` 确保编译通过
   - 前端：`cd chatcode-frontend && npm run build` 确保构建通过
   - 如改动涉及测试，运行 `./mvnw test` 确保全部通过

5. **提交并推送**到你的 fork：

   ```bash
   git add .
   git commit -m "feat: 新增 xxx 功能"
   git push origin 你的分支名
   ```

6. **发起 Pull Request**，在 PR 描述中说明：
   - 改动内容与动机（关联的 issue 编号）
   - 改动前后的行为差异
   - 如何验证改动

## 分支命名规范

| 前缀 | 用途 | 示例 |
|------|------|------|
| `feat/` | 新功能 | `feat/add-export-excel` |
| `fix/` | 缺陷修复 | `fix/chat-stream-timeout` |
| `docs/` | 文档改动 | `docs/update-readme` |
| `test/` | 测试补充 | `test/add-app-controller-tests` |
| `refactor/` | 代码重构 | `refactor/ai-tool-registry` |
| `chore/` | 构建/依赖/配置 | `chore/add-github-actions` |

## 提交信息规范

使用 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/) 格式：

```
<type>(<scope>): <描述>
```

| type | 含义 |
|------|------|
| `feat` | 新功能 |
| `fix` | 修复 bug |
| `docs` | 文档 |
| `test` | 测试 |
| `refactor` | 重构（不改变行为） |
| `perf` | 性能优化 |
| `chore` | 构建、依赖等杂项 |

示例：

```
feat: 支持生成 Vue 项目
fix(chat): 修复流式输出中断问题
docs: 补充部署说明
test: 为应用管理接口补充单元测试
```

## Pull Request 要求

- 一个 PR 只做一件事，保持改动小而聚焦，便于 review
- 所有代码必须通过编译与测试
- 不要提交 IDE 配置、构建产物（`target/`、`node_modules/`、`dist/` 等）
- 涉及 AI 模型调用的改动，请注明已实际验证
- PR 标题遵循提交信息规范

## 代码风格

- **Java**：遵循项目现有风格，使用 Lombok 简化样板代码，包名以 `com.zhuPian` 开头
- **前端**：遵循 ESLint + Prettier 配置，提交前执行 `npm run lint` 与 `npm run format`
- 新增公共逻辑请补充必要的注释，命名使用有意义的英文

## 遇到问题？

可以 [提 issue](https://github.com/zhupian/ai-code-generator/issues) 讨论想法、报告 bug，也可以在 PR 中直接交流。任何讨论都欢迎！
