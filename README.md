# 好好学习 (Study Well)

> 陪伴学习，让专注有回报。

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](./LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.2-brightgreen.svg)](./CHANGELOG.md)
[![Platform](https://img.shields.io/badge/platform-Web_%7C_Android-lightgrey.svg)](#)

## 项目简介

「好好学习」是一款纯前端、本地化运行的 AI 专注力培养与学习管理工具。它通过浏览器端 AI 姿态检测、番茄钟计时、积分激励体系和管理员后台，帮助用户建立专注习惯。

本项目采用单文件架构，所有数据（包括录音、抓拍图片）均存储在客户端本地（LocalStorage + IndexedDB），无需后端服务器支持，保护用户隐私并支持完全离线使用。

### 设计理念

本应用仅作为辅助工具，不建议以此强制他人使用。过度使用监督、惩罚等功能可能带来心理压力。建议多沟通、多鼓励，把工具当作参考而非评判标准。身心健康比任何数据都重要。

## 核心功能

- **AI 姿态检测**：基于 face-api.js，实时识别专注、低头、离座、趴桌等状态，提供视觉与听觉反馈。
- **双模式计时**：支持自由模式与挑战模式，适配不同学习场景。
- **积分激励体系**：通过学习赚取积分，在商店兑换奖励，由管理员确认兑现，形成正向闭环。
- **中英诵读**：内置素材库，支持录音提交与后台审核评分。
- **数学强化**：5 级难度自适应出题，支持限时答题训练。
- **隐私安全**：纯本地存储，无任何数据上传行为。
- **离线可用**：Web 版为单 HTML 文件，APK 版内置全部资源，断网环境下功能完整。
- **游戏化体验**：连击特效、徽章解锁、彩纸庆祝动画，提升专注趣味性。

## 在线体验与下载

| 平台 | 获取方式 | 说明 |
| :--- | :--- | :--- |
| Web 版 | [GitHub Pages 在线演示](https://isnp.github.io/StudySentry/) | 推荐使用 Chrome / Edge / Safari |
| Android APK | [Releases 页面下载](../../releases/latest) | 基于 HBuilderX 打包，支持原生权限调用 |

> 注意：摄像头与麦克风 API 仅在 localhost 或 HTTPS 环境下可用。直接双击打开 HTML 文件时，部分浏览器可能限制媒体权限。

## 技术架构

| 模块 | 技术方案 | 说明 |
| :--- | :--- | :--- |
| AI 推理 | face-api.js (TinyFaceDetector) | 浏览器端实时人脸关键点检测 |
| 数据存储 | LocalStorage + IndexedDB | LS 存元数据，IDB 存 Blob 大文件 |
| 路由系统 | Hash Router | 纯前端 SPA，兼容 file:// 协议 |
| UI 框架 | CSS Variables + Flex/Grid | 零框架依赖，响应式移动端适配 |
| 音频处理 | MediaRecorder + AudioContext | 录音采集与交互音效反馈 |
| 动画效果 | canvas-confetti + CSS Keyframes | 庆祝特效与微交互动画 |
| App 打包 | HBuilderX (uni-app WebView) | 桥接原生权限，封装为独立 APK |

## 使用的开源项目
face-api.js	@vladmandic
canvas-confetti	@catdad
Font Awesome Free	Fonticons, Inc.
Google Fonts	Google
jsDelivr	Prospect One

## 开发致谢
Deepseek

### 存储策略

- **LocalStorage**：存储配置、积分、学习记录等结构化数据。
- **IndexedDB**：存储朗读录音（Blob）、违纪抓拍图片（Blob）。
- **自动清理**：当存储接近阈值时，按优先级自动淘汰旧数据，防止配额溢出。

## 本地开发

```bash
# 克隆仓库
git clone https://github.com/your-username/study-well.git
cd study-well

# 使用任意静态服务器启动（需 HTTPS 或 localhost 以获取媒体权限）
npx serve .
# 或
python3 -m http.server 8080


