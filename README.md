# Usart_02 — UART 中断接收 HEX 格式回显

基于 STM32U575VGT6 的 UART 中断接收示例，将接收到的每个字节以十六进制格式回显到 PC。

## 硬件平台

- **MCU:** STM32U575VGT6 (Cortex-M33, LQFP100)
- **开发环境:** STM32CubeIDE / Keil MDK-ARM

## 外设使用

| 外设 | 配置 | 引脚 |
|------|------|------|
| USART1 | 115200 8N1, 中断模式 | PA9 (TX) / PA10 (RX) |

## 功能说明

1. 使用 `HAL_UART_Receive_IT` 中断驱动单字节接收
2. 回调函数置标志位 `rx_flag`
3. 主循环检测标志后，将接收字节格式化为 HEX 字符串回传

**示例：** 发送字符 `'A'` (0x41) → 收到回显 `0x41\r\n`

## 技术特点

- 中断接收 + 标志位通知模式
- `fputc` 重定向实现 `printf` 通过 USART1 输出（Keil MicroLIB）
- 适合学习 STM32U5 平台 UART 中断接收机制
