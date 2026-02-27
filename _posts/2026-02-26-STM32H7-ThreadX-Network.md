---
layout: post
title: "STM32H7 ThreadX NetX Duo 网络移植"
date: 2026-02-26 12:00:00 +0000
categories: ThreadX STM32 NetX_Duo
---

# STM32H7 ThreadX NetX Duo 网络移植

本文介绍如何在 STM32H7 微控制器上移植 Azure RTOS ThreadX 和 NetX Duo 网络协议栈。

## 硬件平台

- STM32H743/753
- Ethernet PHY (LAN8742A)

## 软件组件

- ThreadX RTOS
- NetX Duo TCP/IP Stack
- STM32CubeMX 配置

## 移植步骤

### 1. CubeMX 配置

使用 STM32CubeMX 配置 ETH 外设和 FreeRTOS（或 ThreadX）。

### 2. 添加 NetX Duo

在项目中集成 NetX Duo 源码，配置网络参数。

### 3. 驱动实现

实现 Ethernet 驱动接口，包括数据收发DMA配置。

## 测试结果

成功实现 TCP/UDP 通信，验证了网络功能正常工作。
