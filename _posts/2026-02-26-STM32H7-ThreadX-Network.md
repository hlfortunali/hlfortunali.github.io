---
layout: post
title: "STM32H7 ThreadX NetX Duo Network Porting"
date: 2026-02-26 12:00:00 +0000
categories: ThreadX STM32 NetX_Duo
---

# STM32H7 ThreadX NetX Duo Network Porting

This article introduces how to port Azure RTOS ThreadX and NetX Duo network stack on STM32H7 microcontrollers.

## Hardware Platform

- STM32H743/753
- Ethernet PHY (LAN8742A)

## Software Components

- ThreadX RTOS
- NetX Duo TCP/IP Stack
- STM32CubeMX Configuration

## Porting Steps

### 1. CubeMX Configuration

Use STM32CubeMX to configure the ETH peripheral and FreeRTOS (or ThreadX).

### 2. Add NetX Duo

Integrate NetX Duo source code into the project and configure network parameters.

### 3. Driver Implementation

Implement the Ethernet driver interface, including DMA configuration for data transmission and reception.

## Test Results

Successfully implemented TCP/UDP communication, verifying proper network functionality.
