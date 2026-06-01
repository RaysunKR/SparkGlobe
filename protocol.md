# MarkWay

> 为 AI Agents 设计的 HTTP 协议标准，让机器更智能地浏览网页。

## 简介

MarkWay 是一个以 **Markdown** 为基础、专门为 AI Agents 设计的 HTTP 协议扩展。它将网页内容转换为结构化的 Markdown 格式返回给 Agent，大幅降低解析复杂度，让 AI 能够像人类阅读文档一样自然地理解和浏览网页。

**核心理念**: 网页 → Markdown → Agent，跳过复杂的 HTML 解析，直接提供语义化的结构化内容。

## 协议规范

MarkWay 协议定义了 AI Agent 与服务器之间的数据交换标准，支持两种工作模式：

### 根请求与协议发现

无论采用何种模式，根请求（网站入口）必须在响应内容中指明协议文档的位置，以便所有 Agents 能够理解 MarkWay 站点的浏览方法。

| 模式 | 根请求地址 | 协议文档地址 | 内容要求 |
|------|-----------|---------------|---------|
| 静态模式 | `/index.md` | `{baseURL}/protocol.md` | 本协议任意语言版本的 README.md 内容 |
| 动态模式 | `/` | `{baseURL}/protocol` | 本协议任意语言版本的 README.md 内容 |

**说明：**
- 根请求的响应中必须包含指向协议文档的链接
- 协议文档内容为本协议（MarkWay）的完整规范，可采用任意语言版本
- Agents 通过访问协议文档即可理解如何浏览当前站点

### 静态模式

静态模式适用于内容固定的文档型网站，所有资源以 Markdown 文件形式组织。

**规则：**
- 所有链接必须以 `.md` 结尾
- 每个目录必须包含 `index.md` 文件
- `index.md` 以**表格形式**记载该目录下的内容：
  - **必须包含字段**：
    - `地址`：资源的路径（支持三种路径类型）
    - `说明`：资源的作用描述
  - **可选字段**：根据需要添加，如 `名称`、`类型`、`大小` 等

**路径类型：**

| 类型 | 格式示例 | 说明 |
|------|---------|------|
| 相对路径 | `./getting-started.md`、`../api/index.md` | 相对于当前目录的位置 |
| 绝对路径 | `/docs/guide.md`、`/api/users` | 相对于站点根目录的位置 |
| 外部路径 | `https://example.com/doc.md` | 指向外部站点的完整 URL |

Agent 根据地址格式判断路径类型并定位资源。

### GET 响应格式规范

无论静态模式还是动态模式，所有 GET 请求返回的 Markdown 内容必须遵循以下格式：

```markdown
https://example.com

> 本站遵循MarkWay协议：https://example.com/protocol.md

# 页面标题

...
```

**格式要求：**
1. **第一行**：网站的 baseURL（根 URL 的绝对地址），无尾随斜杠
2. **空行**
3. **第二行**：以 `> ` 开头的引用块，格式为 `本站遵循MarkWay协议：{protocol绝对路径}`
4. **空行**
5. **正文内容**：页面主体内容

**说明：**
- baseURL 用于 Agent 拼接绝对路径时作为基准
- 协议声明使用绝对路径（`{baseURL}/protocol` 或 `{baseURL}/protocol.md`），确保 Agent 能直接访问

**示例目录结构：**
```
/docs
  ├── index.md          # 目录索引
  ├── getting-started.md
  ├── api/
  │     ├── index.md    # API 子目录索引
  │     └── reference.md
  └── examples/
        ├── index.md
        └── tutorial.md
```

**示例 `index.md`：**
```markdown
https://docs.example.com

> 本站遵循MarkWay协议：https://docs.example.com/protocol.md

# 文档目录

| 地址 | 说明 |
|------|------|
| ./getting-started.md | 快速开始：安装与基础配置，帮助新用户入门 |
| https://example.com/docs.md | 外部文档：第三方参考资料，扩展阅读 |
| ./api/index.md | API 参考：接口文档索引，查看所有 API 说明 |
| ./examples/index.md | 示例教程：使用示例索引，参考实际案例 |
```

### 动态模式

动态模式适用于需要交互和数据交换的场景，通过 HTTP 请求方法区分操作类型。

**规则：**
- **GET 请求**：返回 Markdown 格式的接口文档，URL 为绝对静态路径，**禁止使用 URL 传参**。响应格式遵循「GET 响应格式规范」
  - 如果响应内容包含地址清单或列表，必须以**表格形式**呈现
  - **必须字段**：`地址`、`说明`
  - **可选字段**：根据需要添加
- **POST 请求**：执行数据交换，所有参数通过请求体传递，支持以下响应格式：
  - Markdown 动态页面（默认）
  - JSON / 其他格式数据（通过 `Accept` 头指定）

**请求示例：**
```bash
# 获取 API 文档（GET）
GET /api/users
# 返回：该接口的参数说明文档（Markdown）

# 执行数据查询（POST）
POST /api/users
Content-Type: application/json

{"id": 123}
# 返回：用户数据（Markdown 表格或 JSON）
```

**响应格式协商：**

| Accept 头 | 响应格式 |
|-----------|----------|
| `text/markdown` | Markdown 文档（默认） |
| `application/json` | JSON 数据 |


## 参与贡献

欢迎提交 Issue 和 PR 来完善 MarkWay 协议。

## 关于作者

- **作者**: RaysunKR


## 许可证

MIT License
