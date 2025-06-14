<div align="center">
  <img src="assets/logo/Creative PromptX Duck Logo 4.svg" alt="PromptX Logo" width="120" height="120"/>
  <h1>PromptX · AI-native Professional Capability Enhancement System</h1>
  <p>Provides specialized roles, memory management, and knowledge systems for AI applications through MCP protocol. One command to transform any AI client into a professional powerhouse.</p>

  <!-- Badges -->
  <p>
    <a href=" "><img src="https://img.shields.io/github/stars/Deepractice/PromptX?style=social" alt="Stars"/></a>
    <a href="https://www.npmjs.com/package/dpml-prompt"><img src="https://img.shields.io/npm/v/dpml-prompt?color=orange&logo=npm" alt="npm version"/></a>
    <a href="LICENSE"><img src="https://img.shields.io/github/license/Deepractice/PromptX?color=blue" alt="License"/></a>
    <a href="https://github.com/Deepractice/PromptX/actions"><img src="https://img.shields.io/github/actions/workflow/status/Deepractice/PromptX/ci.yml?label=CI&logo=github" alt="CI Status"/></a>
  </p>
  
  <p>
    <a href="README.md">中文</a> | 
    <strong><a href="README_EN.md">English</a></strong> | 
    <a href="https://github.com/Deepractice/PromptX/issues">Issues</a>
  </p>
</div>

---

### ✨ **Understanding PromptX at a Glance**

What can PromptX do? Simply put, it gives your AI assistant a "brain" and "memory."

- **🎭 Professional Role-Playing**: Provides expert roles across different domains, making AI responses more professional and in-depth.
- **🧠 Long-term Memory & Knowledge Base**: AI can remember key information and your preferences, providing coherent and personalized support in ongoing conversations and work.
- **🔌 Easy Integration**: With just one command, seamlessly enable these powerful features for dozens of mainstream AI applications (like Claude, Cursor).

<br/>

### 📸 **Usage Effects After Configuration**

#### **1. Discover and Activate Professional Roles**
*Use `promptx_hello` to discover available roles, then `promptx_action` to activate them, instantly transforming your AI into a domain expert.*
<img src="assets/role-discovery.png" alt="Role Discovery and Activation" width="80%">

#### **2. Intelligent Memory**
*Use `promptx_remember` to save key information, and AI will proactively apply this knowledge in subsequent interactions.*
<img src="assets/remember.png" alt="Memory Feature" width="80%">

---

## 🚀 **Quick Start - 30-Second Setup**

Open your configuration file and copy the `promptx` configuration code below. This is the simplest **zero-configuration mode**, where PromptX automatically handles everything for you.

```json
{
  "mcpServers": {
    "promptx": {
      // Use npx to run promptx service
      "command": "npx",
      // '-y' auto-confirm, '-f' force refresh cache, 'dpml-prompt@snapshot' use latest version, 'mcp-server' start service
      "args": ["-y", "-f", "dpml-prompt@snapshot", "mcp-server"]
    }
  }
}
```

**🎯 It's that simple!** Save the file and restart your AI application, and PromptX is successfully activated.

🔧 If you want to specify a particular folder as PromptX's workspace, you can add the `env` environment variable.

```json
{
  "mcpServers": {
    "promptx": {
      "command": "npx",
      "args": ["-y", "-f", "dpml-prompt@snapshot", "mcp-server"],
      "env": {
        // PROMPTX_WORKSPACE: Custom workspace path (optional, automatically detected by default)
        // Windows: "D:\\path\\to\\your\\project" (note the double backslashes)
        // macOS/Linux: "/Users/username/path/your/project"
        "PROMPTX_WORKSPACE": "/your/custom/workspace/path"
      }
    }
  }
}
```

<br/>

---

### ⚙️ **How It Works**

PromptX acts as a "professional capability middleware" between you and your AI application, communicating through the standard [MCP protocol](https://github.com/metacontroller/mcp).

```mermaid
graph TD
    subgraph "Your AI App (Claude,Cursor,etc.)"
        A[👨‍💻 User Interaction]
    end

    subgraph "PromptX MCP Server"
        C{PromptX Engine}
        D[🎭 Role Library]
        E[🧠 Memory & Knowledge]
    end

    A -- "Calls 'promptx_...' tools" --> B(MCP Protocol)
    B --> C
    C -- "Accesses" --> D
    C -- "Accesses" --> E

    subgraph "Enhanced Response"
        F[✨ Professional Output]
    end
    C --> F
```

When you call the `promptx_...` series of tools, your AI application sends the request via the MCP protocol to PromptX. The PromptX engine loads the appropriate professional roles, retrieves relevant memories, and then returns a professionally enhanced result to your AI application, which is ultimately presented to you.

---

### New to MCP? [Watch MCP Tutorial on BiliBili](https://www.bilibili.com/video/BV1HFd6YhErb)

#### **Supported AI Applications**

| Application | Status | Configuration | Notes |
|-------------|--------|---------------|-------|
| **Claude Desktop** | ✅ Official | Windows: `%APPDATA%\Claude\claude_desktop_config.json`<br/>macOS: `~/Library/Application Support/Claude/claude_desktop_config.json` | Anthropic's official client with native MCP support |
| **Cursor** | ✅ Supported | MCP settings panel | Developer-friendly code editor |
| **Claude Code** | ✅ Supported | `/home/user/.claude.json` or `~/.claude.json` | Anthropic's official CLI tool with native MCP support, command-line AI programming assistant |
| **Windsurf** | ✅ Supported | IDE MCP panel | Codeium's AI-native IDE |
| **Cline** | ✅ Supported | VS Code plugin config | Powerful AI programming assistant |
| **Augment** | ✅ Supported | Desktop app config | AI-native code editor |
| **Trae** | ✅ Supported | IDE plugin config | AI-driven code generation tool |
| **通义灵码** | 🟡 Planned | Alibaba Cloud IDE plugin | Alibaba's AI programming assistant |
| **Zed** | ✅ Supported | Config: `~/.config/zed/settings.json` | High-performance code editor |
| **Continue** | ✅ Supported | VS Code plugin config | VS Code AI assistant plugin |
| **Replit Agent** | 🟡 Experimental | Built into Replit platform | Online programming environment |
| **Jan** | 🟡 In Development | Local AI client | Privacy-first local AI assistant |
| **Ollama WebUI** | 🟡 Community | Third-party MCP adapter | Local model interface |
| **Open WebUI** | 🟡 Community | Plugin system | Open source AI interface |
| **百度 Comate** | 🟡 Planned | Baidu IDE plugin | Baidu's AI programming assistant |
| **腾讯 CodeWhisperer** | 🟡 Planned | Tencent Cloud IDE | Tencent's AI programming tool |

> **Legend**:
> - ✅ **Official Support**: Native or official plugin support for MCP protocol.
> - 🟡 **Experimental/Community/Planned Support**: Support through community plugins, experimental features, or in development plans.
> - More AI applications are integrating MCP protocol...

**🎯 After configuration, your AI application will automatically gain 6 professional tools:**
- `promptx_init`: 🏗️ **System Initialization** - Automatically prepares the working environment.
- `promptx_hello`: 👋 **Role Discovery** - Browse all available expert roles.
- `promptx_action`: ⚡ **Role Activation** - Transform into an expert in a specific domain with one click.
- `promptx_learn`: 📚 **Knowledge Learning** - Have AI learn specific knowledge or skills.
- `promptx_recall`: 🔍 **Memory Retrieval** - Look up historical information from the memory repository.
- `promptx_remember`: 💾 **Experience Saving** - Store important information in long-term memory.

📖 **[Complete MCP Integration Guide](docs/mcp-integration-guide.md)**

---

## 📋 **Practice Cases: Legacy Lands Library**

<div align="center">
  <img src="https://raw.githubusercontent.com/LegacyLands/legacy-lands-library/main/logo.png" alt="Legacy Lands Library Logo" width="120" style="border-radius: 10px; margin: 15px 0 25px 0;">
</div>

#### 📖 Project Overview

**Project Name:** Legacy Lands Library  
**Project URL:** https://github.com/LegacyLands/legacy-lands-library  
**Project Description:** legacy-lands-library is a development toolkit library for modern Minecraft server plugin development. It aims to provide developers with a cross-platform, production-ready infrastructure.

#### 🏢 Organization Information

**Organization Name:** Legacy Lands Development Team  
**Official Website:** https://www.legacylands.cn/  
**Organization Description:** Legacy Lands is an innovative team focused on building large-scale Minecraft civilization simulation experiences. They participate in the open-source community, providing elegant, efficient, and reliable solutions for Minecraft server plugin development and other domains.

> #### **💡 Core Developer Experience**
> "The development experience with PromptX is truly different. Our team, using Claude Code combined with PromptX, had one developer complete over eleven thousand lines of high-quality Java code in just three days.
>
> The value of this workflow is fully demonstrated in actual development. PromptX solves many pain points in AI usage, consistently ensuring code style uniformity and quality standards, greatly reducing the learning curve for new team members. Best practices that previously required repeated communication and documentation inheritance can now naturally integrate into every code generation."

#### **📚 Related Resources**

- **AI Integration Standards and Practice Guide:** https://github.com/LegacyLands/legacy-lands-library/blob/main/AI_CODE_STANDARDS_ZHCN.md

---

## ⭐ **Star Growth Trend**

[![Star History Chart](https://api.star-history.com/svg?repos=Deepractice/PromptX&type=Date)](https://star-history.com/#Deepractice/PromptX&Date)

---

### **🤝 Contributing and Communication**

We welcome any form of contribution and feedback!

- 🌿 **[Branching Strategy](docs/BRANCHING.md)** - Branch management and release process  
- 🚀 **[Release Process](docs/RELEASE.md)** - Version management and release documentation

Join our technical community:

<img src="assets/qrcode.jpg" alt="Technical Community" width="200">

---

## 📄 **License**

[MIT License](LICENSE) - Making AI professional capabilities accessible

---

**🚀 Get Started Now: Launch PromptX MCP Server and enhance your AI application with professional capabilities!**

```