<div align="center">

  <h1>TTHSD Next (TT High Speed Downloader)</h1>
  <p>一个高性能、跨平台、多语言可调用的下载引擎内核</p>
  <img src="https://img.shields.io/badge/Rust-1.75+-orange.svg" alt="Rust Version">
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS%20%7C%20Android%20%7C%20HarmonyOS-blue.svg" alt="Platform">
  <img src="https://img.shields.io/badge/License-GPL--3.0-green.svg" alt="License">

</div>

---

## 📖 关于我们

TTHSD Core 是一个致力于构建**高性能、跨平台、多语言兼容**的下载引擎内核的开源组织。我们的核心产品 **TTHSD Next** 使用 Rust 语言开发 （旧版本使用 Golang 语言开发，现在旧版已停止开发），为各类应用提供专业级的文件下载能力。

### ✨ 核心特性

- ⚡ **极致性能** - 多线程并发下载，全面压榨带宽
- 🌍 **全平台支持** - Windows、Linux、macOS、Android、HarmonyOS
- 🌐 **多语言生态** - 原生支持 Rust、C/C++/C#、Python、Java/Kotlin、ts(Node.js)、Godot
- 💾 **断点续传** - 支持暂停、中断和恢复下载
- 📊 **实时监控** - 实时进度和下载速度反馈
- 🔌 **多种回调方式** - 支持 WebSocket、Socket 和原生函数回调
- 🧠 **零 GC 停顿** - Rust 原生实现，无垃圾回收卡顿
- 🎯 **极低内存占用** - 稳定运行在十几 MB 内存级别

---

## 🏢 组织仓库

### 核心项目

| 仓库 | 描述 | 状态 |
|------|------|------|
| [TTHSDNext](https://github.com/TTHSDownloader/TTHSDNext) | Rust 实现的高性能下载引擎核心 | ✅ 活跃开发 |
| [TTHighSpeedDownloader](https://github.com/TTHSDownloader/TTHighSpeedDownloader) | Golang 实现的前代版本 | ⚠️ 已停止 |

### 语言绑定

| 语言 | 仓库 | 平台 |
|------|------|------|
| 🦀 Rust | [rust](https://github.com/TTHSDownloader/tthsd-interface-rust) | 全平台 |
| 🐍 Python | [scripts/TTHSD_interface.py](https://github.com/TTHSDownloader/TTHSDNext/tree/main/scripts) | 桌面端 |
| ☕ Java/Kotlin | [java/kt](https://github.com/TTHSDownloader/tthsd-interface-kt) | 桌面 + Android |
| 🔷 C# | [csharp](https://github.com/TTHSDownloader/tthsd-interface-csharp) | 桌面端 |
| 🟢 Node.js | [nodejs](https://github.com/TTHSDownloader/tthsd-interface-ts) | 全平台 |
| 🎮 Godot | [godot](https://github.com/sxxyrry/tthsd-interface-godot) | 游戏引擎 |
| 🔨 C/C++/C# | [c/cpp/csharp](https://github.com/TTHSDownloader/tthsd-interface-c) | 全平台 |

---

## 🚀 快速开始

### 获取预编译库

从 [Releases](https://github.com/TTHSDownloader/TTHSDNext/releases) 页面下载对应平台的预编译库：

```text
📦 TTHSD_Release.7z
├── desktop/       # Windows/Linux/macOS (DLL/SO/DYLIB)
├── android/       # Android ARM libraries (.so)
├── harmony/       # HarmonyOS ARM library (.so)
└── scripts/       # Python 接口示例
```

### Python 示例

```python
from TTHSD_interface import TTHSDownloader, EventLogger

downloader = TTHSDownloader('./desktop/tthsd.so')
downloader.start_download(
    urls=["https://example.com/file.zip"],
    save_paths=["/tmp/file.zip"],
    thread_count=8,
    chunk_size_mb=2,
    callback=EventLogger()
)
```

### Kotlin 示例

```kotlin
import com.tthsd.TTHSDownloader

TTHSDownloader().use { dl ->
    dl.startDownload(
        urls = listOf("https://example.com/file.zip"),
        savePaths = listOf("/tmp/file.zip"),
        threadCount = 64,
        chunkSizeMB = 10,
        callback = { event, data ->
            println("进度: ${data["Downloaded"]}/${data["Total"]}")
        }
    )
}
```

更多语言示例请查看各语言的绑定文档。

---

## 📦 系统要求

| 平台 | 架构 | 最低要求 |
|------|------|----------|
| Windows | x86_64/ARM64 | Windows 7+ |
| Linux | x86_64/ARM64 | glibc 2.17+ |
| macOS | x86_64/ARM64 | macOS 10.13+ |
| Android | ARMv7/ARM64 | Android 5.0+ (API 21+) |
| HarmonyOS | ARM64 | OpenHarmony SDK |

---

## 📄 许可证

本项目采用 **GNU General Public License v3.0 (GPL-3.0)** 开源协议。这确保了核心下载软件始终保持开源和自由分发的权利。

[查看完整许可证](LICENSE)

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

- 🐛 [报告 Bug](https://github.com/TTHSDownloader/TTHSDNext/issues/new?template=bug_report.md)
- 💡 [功能建议](https://github.com/TTHSDownloader/TTHSDNext/issues/new?template=feature_request.md)
- 📖 [文档改进](https://github.com/TTHSDownloader/TTHSDNext/pulls)

---

## 📞 联系我们

- 📧 Email: [项目维护者](Contact@mail.sxxyrry.qzz.io)
- 🐙 GitHub: [TTHSDownloader](https://github.com/TTHSDownloader)

---

<div align="center">

**⭐ 如果觉得项目对你有帮助，请给我们一个 Star！**

Made with ❤️ by 23XR Studio Team

</div>
