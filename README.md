> STM32F411 + ESP01S + LVGL 触控屏 OpenWrt 路由器监控仪表盘

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS-lightgrey.svg)

## 📖 简介

NetMate 是一个基于 STM32F411CEU6 的嵌入式触控仪表盘，通过 ESP01S Wi-Fi 模块连接 OpenWrt 路由器，实时展示路由器的运行状态和 Wi-Fi 参数。

**核心功能：**
- 📶 实时显示 Wi-Fi 信号强度、信道、频段
- 📊 展示路由器 CPU 负载、内存使用率、在线设备数
- 🔄 触控翻页切换信息面板

## 🛠️ 硬件架构

| 组件 | 型号 | 说明 |
|------|------|------|
| 主控 | STM32F411CEU6 | ARM Cortex-M4F @ 100MHz |
| Flash | W25Q64JVSSIQ | 8MB 外部存储 |
| Wi-Fi | ESP01S | ESP8266 模块，AT 指令控制 |
| 屏幕 | 2.8寸 ILI9341 | SPI 接口，320x240 分辨率 |
| 调试 | J-Link | SWD 调试与烧录 |

## 🧰 软件架构
┌─────────────────────────────────────┐
│ LVGL (UI 框架) │
├─────────────────────────────────────┤
│ FreeRTOS (实时操作系统) │
├─────────────────────────────────────┤
│ STM32 HAL 驱动 (SPI/UART/GPIO) │
├─────────────────────────────────────┤
│ CMake (跨平台构建系统) │
└─────────────────────────────────────┘
