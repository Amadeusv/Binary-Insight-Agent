<p align="center">
  <img src="https://img.shields.io/badge/version-0.3.0--alpha-00f0ff?style=for-the-badge" alt="Version" />
  <img src="https://img.shields.io/badge/license-MIT-00ff41?style=for-the-badge" alt="License" />
  <img src="https://img.shields.io/badge/AI_Agent-Driven-ff00ff?style=for-the-badge" alt="AI Agent Driven" />
  <img src="https://img.shields.io/badge/Platform-Cross_Platform-ffe600?style=for-the-badge" alt="Cross Platform" />
  <img src="https://img.shields.io/badge/Status-Active_Development-ff3366?style=for-the-badge" alt="Status" />
</p>

<br />

```
   ▄▄▄▄▄▄▄▄▄▄▄  ▄▄▄▄▄▄▄▄▄▄▄  ▄▄▄▄▄▄▄▄▄▄▄  ▄▄▄▄▄▄▄▄▄▄▄  ▄▄▄▄▄▄▄▄▄▄▄ 
  ▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌
  ▐░█▀▀▀▀▀▀▀▀▀ ▐░█▀▀▀▀▀▀▀▀▀  ▀▀▀▀█░█▀▀▀▀ ▐░█▀▀▀▀▀▀▀█░▌▐░█▀▀▀▀▀▀▀█░▌
  ▐░▌          ▐░▌               ▐░▌     ▐░▌       ▐░▌▐░▌       ▐░▌
  ▐░█▄▄▄▄▄▄▄▄▄ ▐░█▄▄▄▄▄▄▄▄▄      ▐░▌     ▐░▌       ▐░▌▐░▌       ▐░▌
  ▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌     ▐░▌     ▐░▌       ▐░▌▐░▌       ▐░▌
   ▀▀▀▀▀▀▀▀▀█░▌▐░█▀▀▀▀▀▀▀▀▀      ▐░▌     ▐░▌       ▐░▌▐░▌       ▐░▌
            ▐░▌▐░▌               ▐░▌     ▐░▌       ▐░▌▐░▌       ▐░▌
   ▄▄▄▄▄▄▄▄▄█░▌▐░█▄▄▄▄▄▄▄▄▄      ▐░▌     ▐░█▄▄▄▄▄▄▄█░▌▐░█▄▄▄▄▄▄▄█░▌
  ▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌     ▐░▌     ▐░░░░░░░░░░░▌▐░░░░░░░░░░░▌
   ▀▀▀▀▀▀▀▀▀▀▀  ▀▀▀▀▀▀▀▀▀▀▀       ▀       ▀▀▀▀▀▀▀▀▀▀▀  ▀▀▀▀▀▀▀▀▀▀▀ 
```

<p align="center">
  <strong>跨平台二进制安全分析与逆向辅助工作台</strong><br />
  <sub>Powered by LLM · Multi-Agent Collaboration · MITRE ATT&CK Mapping</sub>
</p>

<br />

---

## 🎯 项目简介

**Binary-Insight-Agent** 是一个利用大语言模型（LLM）长上下文与多 Agent 协同能力构建的新一代二进制安全分析工作台。它从根本上重塑了传统逆向工程的范式——从"人工逐行分析"升级为 **"AI 驱动、Agent 协同、语义理解"** 的智能分析管线。

### 传统逆向工程的痛点

| 痛点 | 传统方式 | Binary-Insight-Agent |
|------|---------|---------------------|
| 反汇编阅读 | 人工逐指令阅读 IDA/Ghidra 输出 | AI 语义级理解，自动标注控制流与数据流 |
| 代码混淆 | 手动跟踪状态变量，还原控制流平坦化 | **Deobfuscator Agent** 自动识别 OLLVM/控制流混淆并还原 |
| 恶意行为识别 | 依赖经验，逐 API 查文档判断 | **VulnAssess Agent** 自动映射 MITRE ATT&CK，生成攻击链图 |
| 多平台适配 | 每个平台需单独学习调用约定与ABI | 统一中间表示（IR），跨 PE / ELF / Mach-O 分析 |
| 分析报告 | 手动撰写，周期长、质量不稳定 | 多 Agent 交叉验证后自动生成结构化研判报告 |

### 核心理念

> **"Don't reverse engineer alone — let Agents do the heavy lifting."**

本项目将传统逆向工作中「反汇编 → 反混淆 → 行为分析 → 漏洞研判」的四个阶段，分别映射到四个协作的 AI Agent，形成一条自动化的分析管线。LLM 的长上下文窗口使得 Agent 能够直接「阅读」反汇编代码，理解函数语义、识别设计模式、推理程序意图——这是传统模式匹配引擎无法企及的能力。

<br />

---

## 🏗️ 核心架构

### Agent 协作工作流

```
┌─────────────────────────────────────────────────────────────────────┐
│                      🧠 Orchestrator Agent                          │
│                   任务调度 · 上下文管理 · 结果融合                       │
└──────┬──────────────────────┬──────────────────────┬────────────────┘
       │                      │                      │
       ▼                      ▼                      ▼
┌──────────────┐    ┌──────────────────┐    ┌──────────────────┐
│  📄 Decoder  │    │  🔓 Deobfuscator │    │  🛡️ VulnAssess   │
│   Agent      │    │     Agent        │    │     Agent         │
├──────────────┤    ├──────────────────┤    ├──────────────────┤
│ · 指令流清洗  │    │ · 混淆模式识别    │    │ · 敏感API拓扑     │
│ · IAT解析    │    │ · CFG平坦化还原   │    │ · MITRE映射       │
│ · 调用约定推断│    │ · 字符串解密      │    │ · 攻击链研判       │
│ · 伪代码生成  │    │ · 不透明谓词消除  │    │ · 风险评分         │
└──────┬───────┘    └────────┬─────────┘    └────────┬─────────┘
       │                     │                       │
       └─────────────────────┼───────────────────────┘
                             │
                             ▼
                ┌────────────────────────┐
                │   📊 多Agent交叉验证     │
                │   共识研判报告生成        │
                └────────────────────────┘
```

### Agent 职责详解

#### 1. Orchestrator Agent — 调度中枢

- **任务分解**：接收二进制文件后，识别其格式（PE/ELF/Mach-O），规划分析策略
- **上下文分发**：向各子 Agent 分发相关代码段和分析上下文
- **结果融合**：收集各 Agent 输出，消除冲突，生成一致性研判结论

#### 2. Decoder Agent — 指令流清洗

- 将原始机器码反汇编为人类可读的汇编/伪代码
- 解析导入地址表（IAT），识别外部 API 调用
- 推断函数边界、调用约定、参数类型
- 输出结构化的中间表示供下游 Agent 消费

#### 3. Deobfuscator Agent — 反混淆引擎

- 检测并识别混淆模式：OLLVM、控制流平坦化、字符串加密、指令替换
- 应用 D-810 风格的反混淆算法还原原始控制流
- 解密异或（XOR）等简单加密的字符串常量
- 消除垃圾代码和不透明谓词

#### 4. VulnAssess Agent — 漏洞研判

- 构建敏感 API 调用拓扑图（如 `VirtualAlloc → WriteProcessMemory → CreateThread`）
- 将行为链映射到 MITRE ATT&CK 框架（Tactics, Techniques, Procedures）
- 综合评估风险评分（Risk Score），输出威胁等级
- 生成结构化的取证分析报告

<br />

---

## 🖥️ 界面预览

<p align="center">
  <em>暗黑赛博朋克风格 · 三面板布局 · 实时 Agent 日志</em>
</p>

```
┌──────────────────┬──────────────────────────────┬──────────────────┐
│                  │                              │                  │
│  📄 DISASSEMBLY  │  🔮 AGENT CONSOLE            │  🛡️ RISK TOPOLOGY│
│      VIEW        │                              │                  │
│                  │  [Orchestrator] [+] 任务初始化  │     ╭─────╮      │
│  ┌────────────┐  │  [Decompiler]   [→] 开始反汇编 │     │ 78  │      │
│  │ Target ▼  │  │  [Deobfuscator] [~] 混淆检测   │     │/100 │      │
│  └────────────┘  │  [VulnAssess]   [!] 风险研判   │     ╰─────╯      │
│                  │                              │  HIGH RISK       │
│  ; sub_1400010A0 │  ...动态输出中...              │                  │
│  push    rbp     │                              │  MITRE ATT&CK    │
│  mov     rbp,rsp │                              │  ┌────────────┐  │
│  call    Virtual │                              │  │ T1055 HIGH │  │
│  Alloc  ; ⚠️    │                              │  │ Process    │  │
│  ...             │                              │  │ Injection  │  │
│                  │                              │  └────────────┘  │
│                  │                              │  ┌────────────┐  │
│  ARCH: x86_64    │                              │  │ T1622 HIGH │  │
│  FORMAT: PE32+   │  Analysis pipeline            │  │ Debugger   │  │
│                  │  complete. ✓                  │  │ Evasion    │  │
│                  │                              │  └────────────┘  │
└──────────────────┴──────────────────────────────┴──────────────────┘
```

> 💡 **本地 Demo 体验**：克隆本项目后，直接在浏览器中打开 `index.html` 即可体验完整的前端交互 Demo（无需任何后端环境）。

<br />

---

## 🚀 快速开始

### 前端 Demo（零依赖体验）

```bash
# 1. 克隆仓库
git clone https://github.com/your-org/Binary-Insight-Agent.git
cd Binary-Insight-Agent

# 2. 直接在浏览器打开
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

无需 `npm install`，无需启动任何后端服务。Demo 页面使用 CDN 加载 React 和 Tailwind CSS，所有数据均为 Mock 数据，开箱即用。

### 完整工作台（开发中）

```bash
# 后端引擎（规划中）
cd engine
pip install -r requirements.txt
python main.py --target ./samples/suspicious_binary.exe

# WebSocket 实时通信
# Agent 日志将通过 WebSocket 推送到前端
```

> ⚠️ 完整的后端分析引擎正在开发中。当前版本提供完整的前端交互 Demo。

<br />

---

## 📂 项目结构

```
Binary-Insight-Agent/
├── index.html               # 前端 Demo 页面（单文件，零依赖）
├── README.md                # 本文件
├── engine/                  # 后端分析引擎（规划中）
│   ├── agents/
│   │   ├── orchestrator.py  # 调度中枢 Agent
│   │   ├── decoder.py       # 指令流清洗 Agent
│   │   ├── deobfuscator.py  # 反混淆引擎 Agent
│   │   └── vuln_assess.py   # 漏洞研判 Agent
│   ├── ir/                  # 中间表示层
│   ├── parsers/             # 二进制格式解析器 (PE/ELF/Mach-O)
│   └── main.py              # 引擎入口
├── samples/                 # 测试样本（不含恶意代码）
└── docs/                    # 文档
```

<br />

---

## 🔬 技术栈

| 层级 | 技术选型 | 说明 |
|------|---------|------|
| 前端 | React 18 + Tailwind CSS | 暗黑赛博朋克风格，三面板布局 |
| 后端引擎（规划） | Python 3.11+ + asyncio | 高性能异步分析管线 |
| AI / LLM | OpenAI-compatible API | 长上下文模型驱动 Agent 推理 |
| 二进制解析 | LIEF / Capstone / Unicorn | PE / ELF / Mach-O 多格式支持 |
| 反混淆 | 自研 D-810 风格算法 | 控制流平坦化还原 + 字符串解密 |
| 威胁情报 | MITRE ATT&CK v15 | 标准化攻击技术映射 |

<br />

---

## 🧪 开发者指南

### 自定义 Mock 数据

修改 `index.html` 中的 `ASM_SAMPLES` 和 `AGENT_LOG_ENTRIES` 对象即可添加新的分析目标或日志条目。

```javascript
// 添加新的分析目标
ASM_SAMPLES['Your Custom Target'] = {
  arch: 'RISC-V',
  format: 'ELF64',
  sections: ['.text', '.data'],
  code: `; Your assembly code here...`
};
```

### 连接真实后端

前端预留了与后端引擎通信的接口设计，通过 WebSocket 即可替换 Mock 数据为真实 Agent 日志流。

<br />

---

## 📜 License

本项目采用 [MIT License](LICENSE) 开源。

<br />

---

## ⚠️ 免责声明

Binary-Insight-Agent 仅用于**合法的安全研究、恶意软件分析和授权渗透测试**。严禁将其用于任何未授权的系统访问、逆向工程受版权保护的商业软件，或任何违反适用法律法规的活动。使用者须自行承担所有责任。

<br />

<p align="center">
  <sub>Built with ❤️ by the Binary-Insight-Agent Team</sub><br />
  <sub>© 2026 — AI-Powered Binary Analysis, Reinvented.</sub>
</p>
