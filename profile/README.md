<div align="center">

  <h1>TLD Core</h1>
  <p>一个高性能、跨平台、多语言可调用的下载引擎内核</p>
  <img src="https://img.shields.io/badge/Rust-1.75+-orange.svg" alt="Rust Version">
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS%20%7C%20Android%20%7C%20HarmonyOS-blue.svg" alt="Platform">
  <img src="https://img.shields.io/badge/License-GPL--3.0-green.svg" alt="License">

</div>

---

## 📖 关于我们

TLD Core 是一个致力于构建**高性能、跨平台、多语言兼容**的下载引擎内核的开源组织。我们的核心产品 **TLD** 使用 Rust 语言开发 （旧版本使用 Golang 语言开发，现在旧版已停止开发），为各类应用提供专业级的文件下载能力。

### ✨ 核心特性

- ⚡ **极致性能** - 多线程并发下载，全面压榨带宽
- 🌍 **全平台支持** - Windows、Linux、macOS、Android、HarmonyOS
- 🌐 **多语言生态** - 原生支持 Rust、C/C++/C#、Python、Java/Kotlin、ts(Node.js)、Godot
- 💾 **断点续传** - 支持暂停、中断和恢复下载
- 📊 **实时监控** - 实时进度和下载速度反馈
- 🔌 **多种回调方式** - 支持 WebSocket、Socket 和原生函数回调
- 🧠 **零 GC 停顿** - Rust 原生实现，无垃圾回收卡顿
- 🎯 **极低内存占用** - 稳定运行在十几 MB 内存级别

### 🌐 支持的下载协议

- **HTTP / HTTPS**: 支持动态工作量窃取的自适应并发分片，并附带针对反爬机制的 TLS 证书指纹伪装能力。
- **HTTP/3 (QUIC)**: 针对支持 ***Alt-Svc: h3*** 头的服务器，进行无缝探查并使用 QUIC UDP 提速。
- **FTP / FTPS**: 提供全功能的带密码登录或匿名服务器文件访问下载能力。
- **BitTorrent / Magnet**: 利用纯 Rust 的 DHT 网络节点构建实现了完整的种子文件解析和磁力链接解析。
- **ED2K (eMule)**: 无需臃肿的电驴客户端，通过底层 HTTP 代理转换技术直接拉取资源。
- **Metalink 4.0 (.meta4)**: XML 镜像元数据深度解析，智能筛选出当前网络最佳镜像优先级后极速下载。

---

## 🏢 组织仓库

### 核心项目

| 仓库 | 描述 | 状态 |
|------|------|------|
| [TLD](https://github.com/TaiLerDownloader/TaiLerDownloader) | Rust 实现的高性能下载引擎核心 | ✅ 活跃开发 |
| [TTHighSpeedDownloader](https://github.com/TaiLerDownloader/TTHighSpeedDownloader) | Golang 实现的前代版本 | ⚠️ 已停止 |

### 语言绑定

| 语言 | 仓库 | 平台 |
|------|------|------|
| 🦀 Rust | [rust](https://github.com/TaiLerDownloader/tthsd-interface-rust) | 全平台 |
| 🐍 Python | [scripts/TTHSD_interface.py](https://github.com/TaiLerDownloader/TaiLerDownloader/tree/main/scripts) | 桌面端 |
| ☕ Java/Kotlin | [java/kt](https://github.com/TaiLerDownloader/tthsd-interface-kt) | 桌面 + Android |
| 🟢 Node.js | [nodejs](https://github.com/TaiLerDownloader/tthsd-interface-ts) | 全平台 |
| 🎮 Godot | [godot](https://github.com/TaiLerDownloader/tthsd-interface-godot) | 游戏引擎 |
| 🔨 C/C++/C# | [c/cpp/csharp](https://github.com/TaiLerDownloader/tthsd-interface-c) | 全平台 |
| 🔨 Golang | [c/cpp/csharp](https://github.com/TaiLerDownloader/tthsd-interface-golang) | 全平台 |

---

## 🚀 快速开始

### 获取预编译库

从 [Releases](https://github.com/TaiLerDownloader/TaiLerDownloader/releases) 页面下载对应平台的预编译库：

```text
📦 TaiLerDownloader_Release.7z
├── desktop/       # Windows/Linux/macOS (DLL/SO/DYLIB)
├── android/       # Android ARM libraries (.so)
├── harmony/       # HarmonyOS ARM library (.so)
└── scripts/       # Python 接口示例
```

### Python 示例

```python
from TLD_interface import TLDownloader, EventLogger

downloader = TLDownloader('./desktop/TaiLerDownloader.so')
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

- 🐛 [报告 Bug](https://github.com/TaiLerDownloader/TaiLerDownloader/issues/new?template=bug_report.md)
- 💡 [功能建议](https://github.com/TaiLerDownloader/TaiLerDownloader/issues/new?template=feature_request.md)
- 📖 [文档改进](https://github.com/TaiLerDownloader/TaiLerDownloader/pulls)

---

## 📞 联系我们

- 📧 Email: [项目维护者](Contact@mail.sxxyrry.qzz.io)
- 🐙 GitHub: [TTHSDownloader](https://github.com/TaiLerDownloader/r)

---

<div align="center">

**⭐ 如果觉得项目对你有帮助，请给我们一个 Star！**

Made with ❤️ by TT23XR Studio Team

</div>
