<div align="center">

<img src="https://img.shields.io/badge/ImmortalWrt-25.12-blue?style=for-the-badge&logo=openwrt" alt="ImmortalWrt">
<img src="https://img.shields.io/badge/SoC-RK3528-orange?style=for-the-badge&logo=arm" alt="RK3528">
<img src="https://img.shields.io/badge/Arch-ARMv8--aarch64-green?style=for-the-badge" alt="ARMv8">

# H28K

**基于 ImmortalWrt 的 H28K (RK3528) 每日自动编译固件**

[![每日编译](https://github.com/Supremeyyds/immortalwrt-h28k/actions/workflows/build.yml/badge.svg)](https://github.com/Supremeyyds/immortalwrt-h28k/actions/workflows/build.yml)
[![Latest Release](https://img.shields.io/github/v/release/Supremeyyds/immortalwrt-h28k?label=最新固件&color=brightgreen)](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)
[![下载量](https://img.shields.io/github/downloads/Supremeyyds/immortalwrt-h28k/total?color=blue&label=总下载量)](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)

[📥 下载固件](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest) · [🐛 提交问题](https://github.com/Supremeyyds/immortalwrt-h28k/issues) · [📖 ImmortalWrt 官方](https://immortalwrt.org)

</div>

---

## 📋 设备信息

| 项目 | 说明 |
|------|------|
| **设备型号** | H28K |
| **处理器** | 瑞芯微 RK3528 (四核 Cortex-A53) |
| **架构** | ARMv8 / AArch64 |
| **固件格式** | squashfs-sysupgrade |
| **上游分支** | [immortalwrt/openwrt-25.12](https://github.com/immortalwrt/immortalwrt/tree/openwrt-25.12) |

## 📦 默认配置

- 默认 IP：`192.168.1.1`
- 默认密码：无（首次登录请设置）
- 管理界面：LuCI (HTTP/HTTPS)
- 包管理器：apk
- 内置 nikki 代理插件

## 📝 自用说明

### 刷机

**首次刷机（从原厂固件）：**
1. 解压 `.img.gz` 得到 `.img`
2. 使用 RKDevTool 进入 Loader 模式，写入 eMMC

**升级：**
1. 登录 LuCI → 系统 → 备份/升级
2. 上传 `.img.gz`，取消勾选"保留配置"，刷写

### 网络接口

| 接口 | 用途 |
|------|------|
| eth0 | LAN |
| eth1 | WAN |

### LED 指示灯

| LED | 颜色 | 说明 |
|-----|------|------|
| work | 绿色 | 系统运行指示 |
| wan | 蓝色 | WAN 口活动 |
| lan | 琥珀色 | LAN 口活动 |

## 🔄 自动更新

本仓库每天北京时间 **11:17** 自动编译，始终跟踪上游最新代码。编译成功后固件会自动上传到 [Releases](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)。

## 🙏 致谢

- [ImmortalWrt](https://github.com/immortalwrt/immortalwrt) — 上游项目
- [OpenWrt](https://openwrt.org) — 基础框架
- [nikki](https://github.com/nikkinikki-org/OpenWrt-nikki) — 代理插件

---

<div align="center">

**如果这个项目对你有帮助，请点个 ⭐ Star 支持一下！**

</div>
