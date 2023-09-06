---
layout: posts
title: Passive Filter
date: 2023-09-05
tags : [analog, circuit, passive device, filter ]
use_math: true
---

전자회로에서 필터란 특정 대역의 신호(Signal)을 통과시키는 것을 말합니다.

Passive Device(수동소자)를 이용한 필터는 오직 신호를 감쇠 합니다. 이때 신호를 2배 감소(-3dB)되는 지점이 Cut off Frequency

$$ Z_C = \frac{1}{2\pi fC}$$

Capacitor에서는 고주파 통과

$$ Z_L = {2\pi fL}$$

Inductor에서는 저주파 통과


# LPF 
LPF(Low Pass Filter)란 저주파만 통과 시키는 필터입니다.



# HPF
HPF(High Pass Filter)란 고주파만 통과 시키는 필터입니다.

# BPF 

BPF(Band Pass Filter)란 특정 주파수 범위(band)를 통과 시키는 필터입니다.