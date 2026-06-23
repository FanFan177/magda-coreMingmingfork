<p align="center">
  <img src="assets/Banner.png" alt="MAGDA" width="400">
</p>

<p align="center">
  <a href="https://github.com/Conceptual-Machines/magda-core/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/Conceptual-Machines/magda-core/ci.yml?label=Linux&logo=linux&logoColor=white" alt="Linux Build"></a>
  <a href="https://github.com/Conceptual-Machines/magda-core/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/Conceptual-Machines/magda-core/ci.yml?label=macOS&logo=apple" alt="macOS Build"></a>
  <a href="https://github.com/Conceptual-Machines/magda-core/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/Conceptual-Machines/magda-core/ci.yml?label=Windows&logo=windows" alt="Windows Build"></a>
  <a href="https://github.com/Conceptual-Machines/magda-core/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-GPL--3.0-blue.svg" alt="License"></a>
  <img src="https://img.shields.io/badge/C%2B%2B-20-blue.svg" alt="C++20">
  <a href="https://crowdin.com/project/magda"><img src="https://badges.crowdin.net/magda/localized.svg" alt="Crowdin"></a>
</p>

<p align="center">
  Multi-Agent Digital Audio
</p>
<p align="center"><img src="assets/treaktion-engine-logo.png" alt="Powered by Tracktion Engine" width="250" height="80"></p>

---

MAGDA是免费的, 一款原生深度集成 AI 的开源数字音频工作站（DAW），基于 C++20、JUCE 框架与 Tracktion 音频引擎开发.

### Features

- **多功能轨道**: 所有轨道同时支持音频片段与 MIDI 片段
- **三视图**: 实时循环乐段网格，走带和混音
- **AI指令**: 自然语言指令可在软件内直接生成并执行自定义领域专用语言（自带密钥接入第三方 API）
- **调制系统**: 每个乐器 / 效果单元与机架均配备 16 个低频振荡器（附带贝塞尔曲线编辑器）及 16 个宏旋钮
- **机架**: 支持多条并行处理链路，每条链路独立配备音量、声像、静音、独奏控制，机架可无限嵌套
- **钢琴窗**: 配备pitchbend和MIDI CC通道
- **鼓机**: device
- **会话视窗**: 支持片段触发播放
- **混音视窗**: 配备音量推子、声像、静音、独奏、效果发送通道以及输入输出信号路由功能
- **可折叠、可自由缩放面板**: 左侧为属性检查器与 AI 对话面板，右侧是插件浏览器与采样素材浏览器，底部为上下文自适应编辑器

### 更多链接

- **官网**: [magda.land](https://magda.land/)
- **YouTube**: [介绍](https://www.youtube.com/watch?v=momhIo5vOSc)
- **KVR**: [发布页](https://www.kvraudio.com/product/magda-by-conceptual-machines)
- **Issues**: [Bug反馈和特性请求](https://github.com/Conceptual-Machines/magda-core/issues)

## 状态

阅读[Issues](https://github.com/Conceptual-Machines/magda-core/issues) 获取已知Bug和计划

## 构建

### Prerequisites

- C++20 标准编译器（GCC 10 及以上、Clang 12 及以上，或 Xcode）
- CMake 3.20 及以上版本
- [Git LFS](https://git-lfs.com/) 必需，用于拉取项目内置二进制资源，如中日韩字体等
  (CJK font, etc.). 下载 `brew install git-lfs` (macOS),
  `apt install git-lfs` (Debian/Ubuntu), or `choco install git-lfs` (Windows),
  then run `git lfs install` once per machine.

### 快速上手

```bash
# Clone with submodules and LFS assets
git clone --recursive https://github.com/Conceptual-Machines/magda-core.git
cd magda-core
git lfs pull  # safety net if git-lfs wasn't installed at clone time

# Setup and build
make setup
make debug

# Run
make run
```

### Make Targets

```bash
make setup      # Initialize submodules and dependencies
make debug      # Debug build
make release    # Release build
make test       # Run tests
make clean      # Clean build artifacts
make format     # Format code
make lint       # Run clang-tidy analysis
```

## Automated Workflows

The project includes automated GitHub Actions workflows:

- **CI Workflow**: Runs on every push to validate builds and code quality
- **Security Scanning**: CodeQL analysis, secret detection, and vulnerability scanning
- **Periodic Code Analysis**: Weekly scans for TODOs, FIXMEs, and code smells
- **Refactoring Scanner**: Bi-weekly analysis of code complexity and technical debt

See [docs/AUTOMATED_WORKFLOWS.md](docs/AUTOMATED_WORKFLOWS.md) for details on automated analysis and periodic workflows.

## Security

MAGDA takes security seriously. The repository implements comprehensive security measures:

- 馃敀 **Branch Protection**: Main branch protected with required reviews and status checks
- 馃攳 **Automated Scanning**: CodeQL security analysis for C++ vulnerabilities
- 馃攼 **Secret Detection**: Automated scanning to prevent credential leaks
- 馃洝锔? **Dependency Monitoring**: Dependabot for security updates
- 鈿? **CI/CD Security**: All security checks must pass before merge

**Found a security issue?** Please review our [Security Policy](SECURITY.md) for responsible disclosure.

For detailed information about branch protection and security architecture, see [docs/BRANCH_PROTECTION.md](docs/BRANCH_PROTECTION.md).

## Architecture

```
magda/
鈹溾攢鈹? daw/        # DAW application (C++/JUCE)
鈹?   鈹溾攢鈹? audio/      # Audio processing
鈹?   鈹溾攢鈹? core/       # Track, clip, selection management
鈹?   鈹溾攢鈹? engine/     # Tracktion Engine wrapper
鈹?   鈹溾攢鈹? interfaces/ # Abstract interfaces
鈹?   鈹溾攢鈹? profiling/  # Performance profiling
鈹?   鈹溾攢鈹? project/    # Project management and serialization
鈹?   鈹溾攢鈹? ui/         # User interface components
鈹?   鈹斺攢鈹? utils/      # Utility helpers
鈹斺攢鈹? agents/     # Agent system (C++)
tests/          # Test suite
scripts/        # Development and build scripts
docs/           # Documentation
```

## Dependencies

- [Tracktion Engine](https://github.com/Tracktion/tracktion_engine) - Audio engine
- [JUCE](https://juce.com/) - C++ application framework (GUI, audio I/O, plugin hosting, MIDI, DSP)
- [juce-llm](https://github.com/Conceptual-Machines/juce-llm) - LLM API client module
- [llama.cpp](https://github.com/ggml-org/llama.cpp) - Embedded local LLM inference
- [Catch2](https://github.com/catchorg/Catch2) - Testing (fetched via CMake)

## Issues

> **提醒:**  MAGDA还在早期v0的开发阶段。始发于2026年1月，先是进行了内部迭代，最近才公开发布。因为开发者们非常活跃，并且我们能预料到肯定会有bug和丢失的部分，所以帮助我们的最好方法就是提交您的问题

发现了一个bug或者有一个特性请求? 请在Github上 [open an issue](https://github.com/Conceptual-Machines/magda-core/issues/new)

## 开源证书

GPL v3 - see [LICENSE](LICENSE) for details.
