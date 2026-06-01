# MarkWay

> An HTTP protocol standard designed for AI Agents, enabling machines to browse the web more intelligently.

## Introduction

MarkWay is a Markdown-based HTTP protocol extension specifically designed for AI Agents. It converts web content into structured Markdown format and returns it to Agents, significantly reducing parsing complexity and allowing AI to understand and browse web pages as naturally as humans read documents.

**Core Concept**: Web → Markdown → Agent, skipping complex HTML parsing and directly providing semantic structured content.

## Protocol Specification

The MarkWay protocol defines data exchange standards between AI Agents and servers, supporting two operating modes:

### Root Request and Protocol Discovery

Regardless of the mode used, the root request (website entry point) must specify the location of the protocol document in its response content, so that all Agents can understand how to browse MarkWay sites.

| Mode | Root Request | Protocol Document Address | Content Requirements |
|------|--------------|---------------------------|---------------------|
| Static Mode | `/index.md` | `{baseURL}/protocol.md` | README.md content of this protocol in any language |
| Dynamic Mode | `/` | `{baseURL}/protocol` | README.md content of this protocol in any language |

**Notes:**
- The root request response must contain a link to the protocol document
- The protocol document contains the complete specification of this protocol (MarkWay), available in any language version
- Agents can understand how to browse the current site by accessing the protocol document

### Static Mode

Static mode is suitable for document-oriented websites with fixed content, where all resources are organized as Markdown files.

**Rules:**
- All links must end with `.md`
- Each directory must contain an `index.md` file
- `index.md` records the contents of the directory in **table format**:
  - **Required fields**:
    - `Address`: The path to the resource (supports three path types)
    - `Description`: A description of the resource's purpose
  - **Optional fields**: Add as needed, such as `Name`, `Type`, `Size`, etc.

**Path Types:**

| Type | Format Example | Description |
|------|---------------|-------------|
| Relative Path | `./getting-started.md`, `../api/index.md` | Position relative to current directory |
| Absolute Path | `/docs/guide.md`, `/api/users` | Position relative to site root |
| External Path | `https://example.com/doc.md` | Full URL pointing to external site |

Agents determine the path type and locate resources based on the address format.

### GET Response Format Specification

Regardless of static or dynamic mode, all Markdown content returned by GET requests must follow this format:

```markdown
https://example.com

> This site follows the MarkWay Protocol: https://example.com/protocol.md

# Page Title

...
```

**Format Requirements:**
1. **First line**: The site's baseURL (absolute root URL), without trailing slash
2. **Empty line**
3. **Second line**: A blockquote starting with `> ` in the format `This site follows the MarkWay Protocol: {protocol_absolute_path}`
4. **Empty line**
5. **Body content**: Main page content

**Notes:**
- baseURL is used by Agents as a base when constructing absolute paths
- Protocol declaration uses absolute path (`{baseURL}/protocol` or `{baseURL}/protocol.md`) to ensure Agents can directly access it

**Example Directory Structure:**
```
/docs
  ├── index.md          # Directory index
  ├── getting-started.md
  ├── api/
  │     ├── index.md    # API subdirectory index
  │     └── reference.md
  └── examples/
        ├── index.md
        └── tutorial.md
```

**Example `index.md`:**
```markdown
https://docs.example.com

> This site follows the MarkWay Protocol: https://docs.example.com/protocol.md

# Documentation Directory

| Address | Description |
|---------|-------------|
| ./getting-started.md | Getting Started: Installation and basic configuration to help new users |
| https://example.com/docs.md | External Docs: Third-party reference materials for extended reading |
| ./api/index.md | API Reference: API documentation index with all API descriptions |
| ./examples/index.md | Examples: Usage examples index with real-world cases |
```

### Dynamic Mode

Dynamic mode is suitable for scenarios requiring interaction and data exchange, distinguishing operation types through HTTP request methods.

**Rules:**
- **GET Request**: Returns Markdown format API documentation, URL is an absolute static path, **URL parameters are prohibited**. Response format follows the "GET Response Format Specification"
  - If the response contains address lists or directories, it must be presented in **table format**
  - **Required fields**: `Address`, `Description`
  - **Optional fields**: Add as needed
- **POST Request**: Executes data exchange, all parameters passed through the request body, supporting the following response formats:
  - Markdown dynamic page (default)
  - JSON / other format data (specified via `Accept` header)

**Request Examples:**
```bash
# Get API documentation (GET)
GET /api/users
# Returns: Parameter documentation for this API (Markdown)

# Execute data query (POST)
POST /api/users
Content-Type: application/json

{"id": 123}
# Returns: User data (Markdown table or JSON)
```

**Response Format Negotiation:**

| Accept Header | Response Format |
|---------------|-----------------|
| `text/markdown` | Markdown document (default) |
| `application/json` | JSON data |


## Contributing

Issues and PRs are welcome to improve the MarkWay protocol.

## About the Author

- **Author**: RaysunKR


## License

MIT License
