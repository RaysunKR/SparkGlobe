# MarkWay

> 為 AI Agents 設計的 HTTP 協議標準，讓機器更智能地瀏覽網頁。

## 簡介

MarkWay 是一個以 **Markdown** 為基礎、專門為 AI Agents 設計的 HTTP 協議擴展。它將網頁內容轉換為結構化的 Markdown 格式返回給 Agent，大幅降低解析複雜度，讓 AI 能夠像人類閱讀文件一樣自然地理解和瀏覽網頁。

**核心理念**: 網頁 → Markdown → Agent，跳過複雜的 HTML 解析，直接提供語義化的結構化內容。

## 協議規範

MarkWay 協議定義了 AI Agent 與伺服器之間的資料交換標準，支援兩種工作模式：

### 根請求與協議發現

無論採用何種模式，根請求（網站入口）必須在回應內容中指明協議文件的位置，以便所有 Agents 能夠理解 MarkWay 站點的瀏覽方法。

| 模式 | 根請求地址 | 協議文件地址 | 內容要求 |
|------|-----------|-------------|---------|
| 靜態模式 | `/index.md` | `{baseURL}/protocol.md` | 本協議任意語言版本的 README.md 內容 |
| 動態模式 | `/` | `{baseURL}/protocol` | 本協議任意語言版本的 README.md 內容 |

**說明：**
- 根請求的回應中必須包含指向協議文件的連結
- 協議文件內容為本協議（MarkWay）的完整規範，可採用任意語言版本
- Agents 通過訪問協議文件即可理解如何瀏覽當前站點

### 靜態模式

靜態模式適用於內容固定的文件型網站，所有資源以 Markdown 文件形式組織。

**規則：**
- 所有連結必須以 `.md` 結尾
- 每個目錄必須包含 `index.md` 文件
- `index.md` 以**表格形式**記載該目錄下的內容：
  - **必須包含欄位**：
    - `地址`：資源的路徑（支援三種路徑類型）
    - `說明`：資源的作用描述
  - **可選欄位`：根據需要添加，如 `名稱`、`類型`、`大小` 等

**路徑類型：**

| 類型 | 格式示例 | 說明 |
|------|---------|------|
| 相對路徑 | `./getting-started.md`、`../api/index.md` | 相對於當前目錄的位置 |
| 絕對路徑 | `/docs/guide.md`、`/api/users` | 相對於站點根目錄的位置 |
| 外部路徑 | `https://example.com/doc.md` | 指向外部站點的完整 URL |

Agent 根據地址格式判斷路徑類型並定位資源。

### GET 回應格式規範

無論靜態模式還是動態模式，所有 GET 請求返回的 Markdown 內容必須遵循以下格式：

```markdown
https://example.com

> 本站遵循MarkWay協議：https://example.com/protocol.md

# 頁面標題

...
```

**格式要求：**
1. **第一行**：網站的 baseURL（根 URL 的絕對地址），無結尾斜線
2. **空行**
3. **第二行**：以 `> ` 開頭的引用塊，格式為 `本站遵循MarkWay協議：{protocol絕對路徑}`
4. **空行**
5. **正文內容**：頁面主體內容

**說明：**
- baseURL 用於 Agent 拼接絕對路徑時作為基準
- 協定聲明使用絕對路徑（`{baseURL}/protocol` 或 `{baseURL}/protocol.md`），確保 Agent 能直接訪問

**示例目錄結構：**
```
/docs
  ├── index.md          # 目錄索引
  ├── getting-started.md
  ├── api/
  │     ├── index.md    # API 子目錄索引
  │     └── reference.md
  └── examples/
        ├── index.md
        └── tutorial.md
```

**示例 `index.md`：**
```markdown
https://docs.example.com

> 本站遵循MarkWay協議：https://docs.example.com/protocol.md

# 文件目錄

| 地址 | 說明 |
|------|------|
| ./getting-started.md | 快速開始：安裝與基礎配置，幫助新用戶入門 |
| https://example.com/docs.md | 外部文件：第三方參考資料，擴展閱讀 |
| ./api/index.md | API 參考：介面文件索引，查看所有 API 說明 |
| ./examples/index.md | 示例教學：使用示例索引，參考實際案例 |
```

### 動態模式

動態模式適用於需要互動和資料交換的場景，通過 HTTP 請求方法區分操作類型。

**規則：**
- **GET 請求**：返回 Markdown 格式的介面文件，URL 為絕對靜態路徑，**禁止使用 URL 傳參**。回應格式遵循「GET 回應格式規範」
  - 如果回應內容包含地址清單或列表，必須以**表格形式**呈現
  - **必須欄位**：`地址`、`說明`
  - **可選欄位**：根據需要添加
- **POST 請求**：執行資料交換，所有參數通過請求體傳遞，支援以下回應格式：
  - Markdown 動態頁面（預設）
  - JSON / 其他格式資料（通過 `Accept` 頭指定）

**請求示例：**
```bash
# 獲取 API 文件（GET）
GET /api/users
# 返回：該介面的參數說明文件（Markdown）

# 執行資料查詢（POST）
POST /api/users
Content-Type: application/json

{"id": 123}
# 返回：用戶資料（Markdown 表格或 JSON）
```

**回應格式協商：**

| Accept 頭 | 回應格式 |
|-----------|----------|
| `text/markdown` | Markdown 文件（預設） |
| `application/json` | JSON 資料 |


## 參與貢獻

歡迎提交 Issue 和 PR 來完善 MarkWay 協議。

## 關於作者

- **作者**: RaysunKR


## 授權條款

MIT License
