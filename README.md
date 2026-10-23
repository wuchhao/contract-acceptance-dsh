# 合同快验（dsh）— 拖入合同 PDF，30 秒生成项目验收单

[![Release](https://img.shields.io/badge/download-latest-blue)](../../releases) [![Powered by DeepSeek](https://img.shields.io/badge/powered%20by-DeepSeek%20CLI-green)]()

**合同快验**（命令行名 `dsh`）是一个本地运行的合同验收单生成工具：拖入合同 PDF，自动解析关键条款，生成结构化的项目验收单，输出 **Word + PDF 双格式**。

单次生成成本约 **¥0.85**（5.8MB 真实合同实测，含 99% 缓存命中）。

> 这是一个"在职工程师的 AI 提效工具"：不是为了替代人，而是把"从 30 页合同里抄字段填模板"这种机械劳动交给模型，人工只做最后核对盖章项。

## 🖼️ 效果演示

| 对话生成 | 确认单成品 |
|---|---|
| ![demo](docs/demo-dialog.png) | ![output](docs/demo-output.png) |

脱敏示例输出见 [`examples/`](examples/) 目录。

## ⬇️ 下载使用

本仓库提供打包好的脚本发行版，无需克隆源码：

1. 前往 [**Releases**](../../releases) 页面，下载最新版 `dsh-acceptance-v1.zip`
2. 解压后按包内 `INSTALL.txt` 操作（核心两步）：
   - 安装 DeepSeek CLI：`npm install -g @deepseek/cli`（Node.js ≥ 18）
   - 配置密钥：`export DEEPSEEK_API_KEY=***`（[platform.deepseek.com](https://platform.deepseek.com) 获取）
3. 运行：

```bash
dsh generate 合同.pdf --template acceptance
```

30 秒内完成解析与生成，Word + PDF 输出到 `./output`，成本约 ¥0.85。

## 📊 实测成本账

| 项目 | 数值 |
|---|---|
| 输入合同 | 5.8MB / 30+ 页 |
| 输入 tokens | ~712 万（含缓存） |
| 缓存命中率 | 99% |
| 单次成本 | **¥0.85** |

## 📁 仓库内容

```
├── README.md          # 本文件
├── examples/          # 脱敏示例输出（验收单成品样例）
└── docs/              # 演示截图
```

脚本发行版（含生成逻辑与验收单模板）见 [Releases](../../releases)。

## ⚠️ 诚实声明

- **人工核对必须保留**：模型抽取的字段准确率不是 100%，金额、工期等关键条款发出前务必人工复核。本工具替代的是"抄写"，不是"审同"
- **领域校准**：提示词按工程类合同调优，其他类型合同（采购、服务）可能需要调整模板字段
- **隐私**：合同文件全程本地解析，仅抽取后的字段文本发送给模型 API；涉密合同请勿用于任何云端 API，自评风险
- **密钥安全**：API Key 仅通过环境变量配置，任何情况下不要写进代码或配置文件

## 🗺️ Roadmap

- [ ] 更多单据模板：投标书摘要 / 工单 / 巡检报告
- [ ] 字段校验规则（金额大写一致性与工期逻辑检查）
- [ ] 批量模式：一个目录的合同一次跑完

## 📜 License

发行版内容供个人与团队内部使用，转载请注明出处。
