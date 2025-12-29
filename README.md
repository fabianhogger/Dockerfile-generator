# 🐳 AI Dockerfile Generator

An intelligent, AI-powered web application that automatically generates production-ready, multi-stage Dockerfiles for your projects. Simply provide your GitHub repository URL or paste your dependency file, and let AI handle the rest!

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://your-demo-url.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## ✨ Features

### 🌍 Multi-Language Support (11 Languages)

Automatically detects and generates optimized Dockerfiles for:

- **Node.js** (`package.json`) - with Next.js, Vite, Express detection
- **Python** (`requirements.txt`, `pyproject.toml`) - with Flask, Django, FastAPI support
- **Go** (`go.mod`) - multi-stage builds with scratch/alpine images
- **Java** - Maven (`pom.xml`) and Gradle (`build.gradle`)
- **Ruby** (`Gemfile`) - with Rails and Sinatra detection
- **Rust** (`Cargo.toml`) - optimized builds with version parsing
- **PHP** (`composer.json`) - with Laravel and Symfony framework detection
- **Elixir** (`mix.exs`) - with Phoenix framework support

### 🔍 Intelligent Detection

- **Dynamic Branch Discovery** - Automatically detects your repository's default branch (no longer limited to main/master)
- **Version Parsing** - Extracts and uses correct language versions from dependency files
- **Framework-Specific Intelligence**:
  - Detects Next.js, Vite, Express for Node.js projects
  - Identifies Flask, Django, FastAPI for Python apps
  - Recognizes Rails, Sinatra for Ruby applications
  - Spots Laravel, Symfony for PHP projects
  - Finds Phoenix framework for Elixir apps
- **Smart Port Detection** - Automatically infers correct ports based on frameworks:
  - Next.js: `3000`
  - Vite: `5173`
  - Flask: `5000`
  - Django/FastAPI: `8000`
  - Phoenix: `4000`
- **Run Command Inference** - Suggests appropriate commands for your framework
- **Subdirectory Scanning** - Explores common directories (`src`, `app`, `server`, `api`, etc.) for better context
- **Monorepo Support** - Detects nested projects in packages, apps, and services directories
- **Existing Dockerfile Detection** - Warns you before overwriting existing Dockerfiles

### ✅ Built-in Validation

Every generated Dockerfile is automatically validated with comprehensive checks:

- ✓ FROM instruction presence
- ⚠️ Warns against using `latest` tag (bad practice)
- ⚠️ Detects untagged base images
- 💡 Suggests `.dockerignore` for `COPY . .` patterns
- 🔒 Security check for non-root USER instruction
- 📝 Validates EXPOSE instruction
- 🎯 Detects and highlights multi-stage builds
- 📊 Shows line count and detailed validation notes

### 🎨 User Experience

- **Two Input Modes**:
  1. **GitHub URL Analysis** - Fetch repository details automatically
  2. **Manual Input** - Paste dependency file content directly
- **Real-time Feedback** - See detected language, version, and framework
- **Validation Reports** - Get actionable recommendations for improvements
- **One-Click Actions**:
  - 📋 Copy to clipboard
  - 💾 Download as file
- **Dark Mode UI** - Optimized for developers
- **Responsive Design** - Works on desktop, tablet, and mobile

## 🚀 Quick Start

### Option 1: Use GitHub URL

1. Enter your GitHub repository URL (e.g., `https://github.com/user/repo`)
2. Click **"Fetch Details"** to auto-detect language and dependencies
3. Review the auto-filled run command and port
4. Click **"Generate Dockerfile"**
5. Copy or download your production-ready Dockerfile!

### Option 2: Manual Input

1. Paste your dependency file content (package.json, requirements.txt, etc.)
2. Specify the run command (e.g., `npm start`, `python app.py`)
3. Optionally specify the port to expose
4. Click **"Generate Dockerfile"**
5. Get your optimized Dockerfile instantly!

## 📋 Examples

### Example 1: Next.js Application

**Input:**
```
GitHub URL: https://github.com/yourusername/nextjs-app
```

**Detection:**
```
✓ Detected: Node.js (Next.js framework)
✓ Version: >=18.0.0
✓ Port: 3000
✓ Run Command: npm start
```

**Output:**
Multi-stage Dockerfile with:
- Build stage with `npm run build`
- Production stage with optimized `node:18-alpine`
- Non-root user for security
- Health checks and proper caching

### Example 2: FastAPI Application

**Input:**
```json
fastapi==0.104.1
uvicorn[standard]==0.24.0
pydantic==2.5.0
```

**Detection:**
```
✓ Detected: Python (FastAPI framework)
✓ Port: 8000
✓ Run Command: uvicorn main:app --host 0.0.0.0 --port 8000
```

**Output:**
Optimized Dockerfile with:
- `python:3.11-slim` base image
- Virtual environment setup
- Dependency caching
- Non-root user
- Health endpoint exposure

### Example 3: Rust Application

**Input:**
```
GitHub URL: https://github.com/yourusername/rust-api
```

**Detection:**
```
✓ Detected: Rust
✓ Version: 1.75
✓ Port: 8080
```

**Output:**
Multi-stage Dockerfile with:
- Builder stage with `rust:1.75-alpine`
- Minimal runtime with `scratch` or `alpine`
- Optimized binary size
- Security-first approach

## 🔧 How It Works

### 1. **Repository Analysis**
   - Fetches repository structure via GitHub API
   - Scans root directory and common subdirectories
   - Identifies dependency files and project structure

### 2. **Intelligent Inference**
   - Analyzes dependency file contents
   - Detects frameworks and their specific requirements
   - Parses version constraints
   - Determines optimal build and run commands

### 3. **AI Generation**
   - Uses Google Gemini AI with expert DevOps prompts
   - Generates production-ready, multi-stage Dockerfiles
   - Follows security best practices
   - Includes helpful comments explaining decisions

### 4. **Validation & Feedback**
   - Runs comprehensive validation checks
   - Provides actionable warnings and suggestions
   - Shows build type (single vs multi-stage)
   - Reports line count and potential improvements

## 🏗️ Best Practices Implemented

All generated Dockerfiles follow industry best practices:

- ✅ **Multi-stage builds** - Minimize final image size
- ✅ **Slim base images** - Use Alpine or slim variants
- ✅ **Layer caching** - Optimize build times
- ✅ **Non-root users** - Enhance security
- ✅ **Specific version tags** - Avoid `latest` tag issues
- ✅ **Dependency separation** - Copy dependencies before code
- ✅ **Build optimization** - Leverage Docker layer caching
- ✅ **Health checks** - Monitor container health (where applicable)
- ✅ **Minimal attack surface** - Only include necessary files

## 🔑 Setup

### Prerequisites

- Google AI API Key ([Get one here](https://aistudio.google.com/app/apikey))

### Configuration

1. Open the application in your browser
2. Enter your Google AI API Key
3. Optionally check "Remember Key" to save it locally
4. Start generating Dockerfiles!

## 🎯 Supported Detection Patterns

| Language | Files Detected | Version Source | Framework Detection |
|----------|----------------|----------------|---------------------|
| Node.js | `package.json` | `engines.node` | Next.js, Vite, Express |
| Python | `requirements.txt`, `pyproject.toml` | `python = "x.x"` | Flask, Django, FastAPI |
| Go | `go.mod` | `go x.x` | Standard library |
| Java | `pom.xml`, `build.gradle` | N/A | Spring Boot (inferred) |
| Ruby | `Gemfile` | `ruby 'x.x'` | Rails, Sinatra |
| Rust | `Cargo.toml` | `rust-version` | Cargo |
| PHP | `composer.json` | `require.php` | Laravel, Symfony |
| Elixir | `mix.exs` | `elixir: "x.x"` | Phoenix |

## 📊 Statistics & Performance

- **Languages Supported:** 11
- **Detection Accuracy:** High (AI-powered inference)
- **Generation Time:** ~2-5 seconds
- **Validation Checks:** 6+ security and best practice rules
- **Branch Detection:** Automatic (main, master, develop, custom)
- **Subdirectory Scanning:** Up to 15 files per common directory

## 🛠️ Technology Stack

- **Frontend:** Vanilla JavaScript (ES6+), HTML5, Tailwind CSS
- **AI Model:** Google Gemini 2.5 Flash
- **APIs:** GitHub API (repository analysis)
- **Architecture:** Single-page application, client-side only

## 🔒 Security & Privacy

- **API Key Storage:** Optional local storage (browser only)
- **No Server:** All processing happens in your browser
- **No Data Collection:** Your code and keys never leave your machine
- **HTTPS Required:** Secure communication with external APIs

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- [ ] Additional language support (Scala, Kotlin, Swift, etc.)
- [ ] Docker Compose generation for multi-container apps
- [ ] .dockerignore file generation
- [ ] Kubernetes manifest generation
- [ ] CI/CD pipeline templates
- [ ] Interactive Dockerfile editor
- [ ] Testing framework detection
- [ ] Environment variable management

## 📝 License

MIT License - feel free to use this in your projects!

## 🙏 Acknowledgments

- Powered by [Google Gemini AI](https://ai.google.dev/)
- Repository analysis via [GitHub API](https://docs.github.com/en/rest)
- UI components with [Tailwind CSS](https://tailwindcss.com/)

## 📞 Support

If you encounter issues or have suggestions:

1. Check existing issues on GitHub
2. Open a new issue with details
3. Provide sample repository URLs for reproduction

---

**Made with ❤️ for developers who want production-ready Dockerfiles in seconds, not hours.**
