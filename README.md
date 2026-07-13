<div align="center">

<img src="https://img.shields.io/badge/ImmortalWrt-25.12-blue?style=for-the-badge&logo=openwrt" alt="ImmortalWrt">&nbsp;
<img src="https://img.shields.io/badge/SoC-RK3528-orange?style=for-the-badge&logo=rockchip" alt="RK3528">&nbsp;
<img src="https://img.shields.io/badge/Arch-ARMv8-aarch64-green?style=for-the-badge" alt="ARMv8">

# HINLINK H28K

**基于 ImmortalWrt 的 HINLINK H28K (RK3528) 每日自动编译固件**

[![每日编译](https://github.com/Supremeyyds/immortalwrt-h28k/actions/workflows/build.yml/badge.svg)](https://github.com/Supremeyyds/immortalwrt-h28k/actions/workflows/build.yml)
[![Latest Release](https://img.shields.io/github/v/release/Supremeyyds/immortalwrt-h28k?label=最新固件&color=brightgreen)](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)
[![下载量](https://img.shields.io/github/downloads/Supremeyyds/immortalwrt-h28k/total?color=blue&label=总下载量)](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)

[📥 下载固件](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest) · [🐛 提交问题](https://github.com/Supremeyyds/immortalwrt-h28k/issues) · [📖 ImmortalWrt 官方](https://immortalwrt.org)

</div>

---

## 📋 设备信息

| 项目 | 说明 |
|------|------|
| **设备型号** | HINLINK H28K |
| **处理器** | 瑞芯微 RK3528 (四核 Cortex-A53) |
| **架构** | ARMv8 / AArch64 |
| **固件格式** | squashfs-sysupgrade |
| **上游分支** | [immortalwrt/openwrt-25.12](https://github.com/immortalwrt/immortalwrt/tree/openwrt-25.12) |

## 🚀 快速开始

### 下载固件

前往 [Releases 页面](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest) 下载最新固件：

```
immortalwrt-rockchip-armv8-hinlink_opc-h28k-squashfs-sysupgrade.img.gz
```

### 刷机方法

**首次刷机（从原厂固件）：**

1. 解压 `.img.gz` 文件得到 `.img`
2. 使用 [RKDevTool](https://github.com/rockchip-linux/rkbin) 进入 Loader 模式
3. 选择固件写入 eMMC

**升级（已刷 OpenWrt/ImmortalWrt）：**

1. 登录 LuCI 管理界面（默认 `http://192.168.1.1`）
2. 进入 **系统 → 备份/升级**
3. 上传 `.img.gz` 固件文件
4. 取消勾选"保留配置"（推荐全新刷入）
5. 点击"刷写固件"

## ⚙️ 编译信息

本仓库使用 **GitHub Actions** 每日自动编译：

```
北京时间每天 11:17 自动执行
  ↓
git clone immortalwrt/openwrt-25.12 最新代码
  ↓
应用 H28K 设备补丁 (DTS / U-Boot / 网络 / LED)
  ↓
更新 feeds (packages / luci / nikki)
  ↓
make defconfig → make -j$(nproc)
  ↓
上传固件到 Releases
```

### 包含的补丁

| 补丁 | 说明 |
|------|------|
| `feeds.conf.default` | 添加 nikki 源 |
| `uboot-rockchip` | 添加 generic-rk3528 U-Boot |
| `rk3528-opc-h28k.dts` | H28K 设备树 |
| `image/armv8.mk` | 固件编译定义 |
| `01_leds` / `02_network` | LED 灯和网络接口配置 |

### 手动编译

```bash
git clone https://github.com/Supremeyyds/immortalwrt-h28k.git
cd immortalwrt-h28k

# 克隆上游源码
git clone -b openwrt-25.12 --single-branch --depth=1 \
  https://github.com/immortalwrt/immortalwrt.git immortalwrt

cd immortalwrt

# 应用补丁
git apply --3way ../patches/0001-opc-h28k.patch

# 更新 feeds
./scripts/feeds update -a
./scripts/feeds install -a

# 应用配置
cp ../.github/configs/opc-h28k.config .config
make defconfig

# 编译
make -j$(nproc) V=s
```

## 📦 默认配置

- 默认 IP：`192.168.1.1`
- 默认密码：无（首次登录请设置）
- 管理界面：LuCI (HTTP/HTTPS)
- 包管理器：apk
- 内置 nikki 代理插件

## 🔄 自动更新

本仓库每天北京时间 **11:17** 自动编译，始终跟踪上游最新代码。编译成功后固件会自动上传到 [Releases](https://github.com/Supremeyyds/immortalwrt-h28k/releases/latest)。

你也可以在 [Actions](https://github.com/Supremeyyds/immortalwrt-h28k/actions) 页面手动触发编译。

## 🙏 致谢

- [ImmortalWrt](https://github.com/immortalwrt/immortalwrt) — 上游项目
- [OpenWrt](https://openwrt.org) — 基础框架
- [nikki](https://github.com/nikkinikki-org/OpenWrt-nikki) — 代理插件

---

<div align="center">

**如果这个项目对你有帮助，请点个 ⭐ Star 支持一下！**

</div>
