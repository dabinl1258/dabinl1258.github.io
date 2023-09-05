---
layout: posts
title: Uart Protocol 
date: 2023-08-30
tags : [digital, uart, protocol ]
---

# UART Protocol Spec
* Serial Protocol
* Asynchronous Full Duplex
* Send LSB Bit First
* IDLE      : High Signal
* Start Bit : Low  Signal 1 Tick
* Stop  Bit : High Signal 1.5 ~ 2 Tick

** Tick (1sec / Boad Rate)


## Timing Diagram 
UART 통신은 비동기 전이중 통신이다. 

CLK선을 사용하지 않는 대신에 송신부와 수신부의 BaudRate을 동일 하게 맞추어준다. 


통신을 하지않는 상태즉 IDLE상태에서는 High을 Tx선에 유지한다. 이후 송신을 시작하면 Low 1 Bit를 1 Tick동안 유지 한다. 


이후 각 Tick마다 LSB인 D0 부터 ~ MSB인 D7까지 전송한다. 

![UART ](/assets/img/Digital/UART-Capture.png)

받는 쪽인 Rx에서는 노이즈를 최소화 하기 위해서 각 Tick의 중간에 데이터를 Capture한다(위 사진의 rx Capture의 Falling Edge).  [Edge Detect활용](/_posts/Digital/2023-08-21-Edge-Detect.md)
## Send 'K' x4B 0b0100 1011 
아래는 ASCII Code 'K'를 전송하는 타이밍도이다.('K'를  LSB first로 2진수 표현 1101 0010)


![Send K Uart](/assets/img/Digital/UART-K-wave.png)

