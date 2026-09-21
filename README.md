# Netmate

基于 STM32F411 的 OpenWrt 路由器状态监控仪表盘。

Netmate 使用 ESP-01S 连接 OpenWrt 路由器，获取路由器运行状态和 Wi-Fi 信息，并通过 ILI9341 触控屏进行展示。项目采用 CMake 构建，支持在 Windows、macOS 和 Linux 上进行开发。

## 功能

- 显示 Wi-Fi 信号强度、信道和频段
- 显示路由器 CPU 负载、内存使用率和在线设备数
- 通过触控操作切换信息页面
- 使用 FreeRTOS 管理任务
- 使用 J-Link 通过 SWD 下载和调试

## 硬件

| 组件 | 型号 | 说明 |
| --- | --- | --- |
| MCU | STM32F411CEU6 | ARM Cortex-M4F，最高 100 MHz |
| 外部 Flash | W25Q64JVSSIQ | 8 MB SPI Flash |
| Wi-Fi | ESP-01S | ESP8266，使用 AT 指令通信 |
| 显示屏 | ILI9341 | 2.8 英寸，320 x 240 |
| 调试器 | J-Link | SWD 下载与调试 |

## 软件架构

- STM32 HAL：GPIO、SPI、I2C、UART、RTC、独立看门狗等外设驱动
- FreeRTOS：实时任务和系统调度
- LVGL：图形界面框架
- CMake：跨平台构建系统
- Ninja：默认构建后端
- ARM GNU Toolchain：默认 ARM GCC 交叉编译工具链
- clangd：C/C++ 代码补全、跳转和静态分析
- Cortex-Debug：VS Code 调试支持

## 开发环境

### 开发工具

- Git
- CMake
- Ninja
- ARM GNU Toolchain
- VS Code
- OpenBCD

### 必须 VS Code 扩展

- CMake Tools
- C/C++ DevTools
- clangd
- Cortex-Debug

## 全平台开发

项目不依赖特定 IDE，可以使用命令行构建编译调试下载，也可配合vscode开发

注意：请在.vscode文件夹中配置对应的插件的路径

## ARM GCC 工具链

默认配置使用 `cmake/gcc-arm-none-eabi.cmake`：

```text
arm-none-eabi-gcc
arm-none-eabi-g++
arm-none-eabi-objcopy
arm-none-eabi-size
```
注意：在macos`brew`安装的版本功能可能不完整，请官网下载完整GNU套件

## 下载与调试

项目提供 VS Code 的 Cortex-Debug 配置，可使用 J-Link 和 OpenOCD 通过 SWD 调试，可以自行切换其他仿真器，自行修改Cortex-Debug 配置。


## STM32CubeMX

部分初始化代码由 STM32CubeMX 生成。 配置详情见`Netmate.ioc` 。
## 开源协议与第三方组件

本项目使用 MIT License。第三方组件按照各自许可证发布，相关许可证文件保存在对应目录中：

- [CMSIS License](Drivers/CMSIS/LICENSE.txt)
- [STM32 HAL License](Drivers/STM32F4xx_HAL_Driver/LICENSE.txt)
- [FreeRTOS License](Middlewares/Third_Party/FreeRTOS/Source/LICENSE)

发布包含第三方组件的源代码或工具时，请保留相应的版权声明和许可证文本。
