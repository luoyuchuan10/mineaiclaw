# ⛏️ Minecraft AI Flat

**一个能看见、能模仿、能陪伴的 Minecraft AI 虚拟玩家 —— 就像你的 Player 2。**

## 简介

Minecraft AI Flat 是一个 Windows 程序。运行后，AI 会作为虚拟玩家加入你的 Minecraft 服务器（Java 版或网页版）。它能看见游戏画面，理解你在做什么，然后像真人一样模仿你的行为：你搭房子它也搭，你挖矿它也挖，你战斗它也帮忙。

内置国产通义千问模型，完全离线运行，保护你的隐私。

## 核心特性

- 支持 Minecraft Java 版 1.8 ~ 1.21+，以及网页版 1.8.8
- 自动扫描局域网内开放 25565 端口的服务器
- 内置通义千问 Qwen3-4B 模型（INT4 量化），内存占用约 3.8GB
- 完全离线运行，无需网络，不上传任何数据
- AI 能看见游戏画面，理解玩家行为并模仿
- 支持自定义皮肤
- 可在设置中切换：内置模型 / 外部 API（如 DeepSeek、OpenAI）
- 8GB 内存电脑即可流畅运行

## 效果示例

你盖木头房子 → AI 在你旁边也盖木头房子
你向下挖矿 → AI 在附近也开始挖矿
你攻击僵尸 → AI 过来帮忙打僵尸
你钓鱼 → AI 拿出鱼竿在旁边钓鱼
你说“来我这边” → AI 移动到你的位置

## 环境要求

- Windows 10 / 11
- Minecraft Java 版服务器（本地或局域网）或网页版 1.8.8 服务器
- 8GB 内存（推荐 16GB）
- 支持 OpenGL 的显卡

## 安装与使用

1. 运行安装器，选择模式：
   - 真·Minecraft Java 版
   - 网页版 Minecraft 1.8.8

2. 安装完成后，运行主程序

3. 程序自动扫描局域网内开放 25565 端口的游戏服务器，从列表中选择一个

4. AI 自动加载内置模型（首次加载稍慢，后续秒开）

5. AI 加入游戏，开始观察和模仿你的行为

6. 可随时打开设置：
   - 切换 AI 模式（内置模型 / 外部 API）
   - 配置 API Key 和地址
   - 更换 AI 玩家皮肤

## 配置文件（config.yaml）

```yaml
# 服务器设置
server_address: auto          # auto 为自动扫描，也可手动填写
server_port: 25565

# Minecraft 版本
minecraft_version: auto       # auto 自动识别，或指定如 1.20.4

# AI 模式
ai_mode: local                # local / api

# 本地模型设置（ai_mode = local 时生效）
model_path: models/qwen/qwen3-4b-int4.gguf

# API 设置（ai_mode = api 时生效）
api_url: https://api.deepseek.com/v1
api_key: your_api_key_here
api_model: deepseek-chat

# 皮肤设置
skin_path: skins/default.png

# 视觉设置
screenshot_interval: 0.5      # 截图间隔（秒）
项目结构
text
Minecraft AI Flat/
├── main.exe
├── config.yaml
├── models/
│   └── qwen/
│       └── qwen3-4b-int4.gguf
├── vision/
│   └── (视觉模型文件)
├── skins/
│   └── default.png
└── assets/
常见问题
Q：需要联网吗？
A：不需要。内置模型完全离线运行。

Q：8GB 内存够用吗？  问：8GB内存够用吗？
A：够用。Qwen3-4B 量化版约占用 3.8GB。

Q：支持哪些 Minecraft 版本？  问：支持哪些Minecraft版本？
A：Java 版 1.8 ~ 1.21+，以及网页版 1.8.8。

Q：AI 能自己玩吗？
A：目前是模仿玩家模式。未来版本会增加独立探索模式。

开源协议
MIT License

致谢
通义千问（Qwen）团队提供的国产大模型

Minecraft 社区

text

---

## 📝 二、完整 TRAE 提示词

```text
# 项目名称：Minecraft AI Flat
# 项目类型：Windows 桌面应用程序 + Minecraft AI 虚拟玩家
# 开发工具：TRAE

## 项目概述

开发一个 Windows 程序（exe），用户安装后运行。程序自动扫描局域网内开放 25565 端口的 Minecraft 服务器（Java版 1.8~1.21+，网页版 1.8.8）。用户选择服务器后，AI 作为虚拟玩家（Player 2）加入游戏。

AI 通过实时截图观察游戏画面，理解玩家正在做什么（搭房子、挖矿、战斗、钓鱼、移动等），然后模仿玩家的行为。内置通义千问 Qwen3-4B 模型，完全离线运行。

---

## 功能清单

### 1. 服务器扫描模块
- 自动扫描局域网内开放 25565 端口的 IP 和端口
- 显示可用服务器列表（含版本信息）
- 支持手动输入服务器地址

### 2. 连接模块
- 支持 Minecraft Java 版 1.8 ~ 1.21+
- 支持网页版 Minecraft 1.8.8（如 Eaglercraft）
- 使用 pyCraft（1.13+）和 mcpi（1.8~1.12）双协议
- AI 以玩家身份加入，可设置自定义皮肤

### 3. 视觉模块
- 使用 mss 或 PIL 实时截取游戏画面
- 截图间隔可配置（默认 0.5 秒）
- 调用轻量视觉模型（如 MiniCPM）生成画面描述
- 输出：玩家位置、玩家动作、周围方块类型、怪物位置等

### 4. 大模型模块
- 内置模型：通义千问 Qwen3-4B（INT4 量化版）
- 模型文件存放于 models/qwen/ 目录
- 使用 llama-cpp-python 加载和推理
- 内存占用约 3.8GB，8GB 内存可运行
- 推理速度 18-32 tokens/秒

### 5. 行为模仿模块
- 模型输入：画面描述 + 最近聊天记录 + 自身状态
