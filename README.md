# 🔐 Security Copilot — VS Code Extension

> Scan your project for vulnerabilities and get AI-powered fix suggestions — runs **100% locally**, no data leaves your machine.

![Version](https://img.shields.io/badge/version-0.0.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![VS Code](https://img.shields.io/badge/VS%20Code-1.85%2B-blueviolet)

-----

## ✨ Features

- 🔍 **Detects OWASP Top 10 vulnerabilities** across your entire project
- 🤖 **AI-powered fix suggestions** via local LLM (no API key needed)
- 🔒 **Fully offline** — your code never leaves your machine
- ⚡ **Supports** JavaScript, TypeScript, Python, Go, Java and more
- 📋 **Detailed report panel** with severity levels and fix suggestions
- 💡 **Inline diagnostics** — squiggly lines on vulnerable code
- 🛠️ **One-click fixes** via CodeLens buttons

-----

## 📋 Requirements

Before using this extension, install the following tools:

### 1. Ollama (for AI fix suggestions)

```bash
# macOS / Linux
curl -fsSL https://ollama.com/install.sh | sh

# Then pull a code model
ollama pull codellama
```

Download for Windows at [ollama.com](https://ollama.com)

### 2. Semgrep (for vulnerability scanning)

```bash
# macOS
brew install semgrep

# Linux / Windows (via pip)
pip install semgrep
```

> **Note:** The extension works in degraded mode (static analysis only) if Ollama is not installed.

-----

## 🚀 Usage

1. Open any project folder in VS Code
1. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
1. Run one of the following commands:

|Command                                 |Description            |
|----------------------------------------|-----------------------|
|`Security Copilot: Scan Current File`   |Scan only the open file|
|`Security Copilot: Scan Entire Project` |Full workspace scan    |
|`Security Copilot: Show Security Report`|Open the report panel  |
|`Security Copilot: Apply Fix`           |Apply a suggested fix  |

-----

## 📊 Vulnerability Severity Levels

|Level     |Description              |
|----------|-------------------------|
|🔴 Critical|Immediate action required|
|🟠 High    |Fix as soon as possible  |
|🟡 Medium  |Fix in next release      |
|🔵 Low     |Best practice improvement|

-----

## 🏗️ How It Works

```
Your Code
    ↓
Semgrep (detects vulnerabilities with precise rules)
    ↓
Local LLM via Ollama (generates human-readable explanations + fixes)
    ↓
VS Code Report Panel + Inline Diagnostics
```

Everything runs locally on your machine. No cloud. No telemetry. No API keys.

-----

## ⚙️ Extension Settings

|Setting                            |Default                 |Description               |
|-----------------------------------|------------------------|--------------------------|
|`securityCopilot.ollamaUrl`        |`http://localhost:11434`|Ollama server URL         |
|`securityCopilot.model`            |`codellama`             |Local model to use        |
|`securityCopilot.scanOnSave`       |`false`                 |Auto-scan on file save    |
|`securityCopilot.severityThreshold`|`medium`                |Minimum severity to report|

-----

## 🛠️ Local Development

```bash
# Clone the repo
git clone https://github.com/your-username/security-copilot
cd security-copilot

# Install dependencies
npm install

# Open in VS Code
code .

# Press F5 to launch Extension Development Host
```

-----

## 🗂️ Project Structure

```
security-copilot/
├── src/
│   ├── extension.ts        # Entry point, command registration
│   ├── scanner.ts          # File collection + Semgrep integration
│   ├── claudeClient.ts     # Local LLM (Ollama) client
│   ├── reportParser.ts     # JSON parsing + validation
│   ├── diagnostics.ts      # Inline squiggly lines
│   ├── codelens.ts         # Fix buttons above vulnerable lines
│   └── webview/
│       ├── panel.ts        # Report panel logic
│       └── report.html     # Report UI
├── package.json
├── tsconfig.json
└── README.md
```

-----

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
1. Create a feature branch (`git checkout -b feature/my-feature`)
1. Commit your changes (`git commit -m 'Add some feature'`)
1. Push to the branch (`git push origin feature/my-feature`)
1. Open a Pull Request

-----

## 🐛 Known Issues

- Large projects (1000+ files) may take a few minutes to scan
- Ollama must be running before launching a scan
- Some minified JS files may produce false positives

-----

## 📅 Changelog

### 0.0.1 — Initial Release

- Basic vulnerability scanning with Semgrep
- AI fix suggestions via Ollama + CodeLlama
- Inline diagnostics and report panel

-----

## 📄 License

MIT — see <LICENSE> for details.

-----

## 🙏 Acknowledgements

- [Semgrep](https://semgrep.dev) — Static analysis engine
- [Ollama](https://ollama.com) — Local LLM runtime
- [CodeLlama](https://github.com/facebookresearch/codellama) — Code understanding model
- [OWASP Top 10](https://owasp.org/www-project-top-ten/) — Vulnerability taxonomy