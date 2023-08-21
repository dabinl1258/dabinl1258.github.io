---
layout: posts
title: Edge Detect Circuit 
date: 2023-08-21
tags : [digital, verilog ]
---

디지털 시스템에서는 한개의 엣지를 입력 받아야 하는 경우가 생긴다.
예를 들어서 UART에서 Start Bit를 감지하는 경우 같은 것이다.

Block Diagram


![Edge Detect Symbol](/assets/img/Digital/Edge-Detect-Symbol.png)

<br>

Flip/Flop의 지연을 이용해서 감지 한다.

다음과 같은 파형이 나와야 한다.


![Edge Detect Wave](/assets/img/Digital/Edge-Detect-Wave.png)

회로도는 다음과 같다.

![Edge Detect Wave](/assets/img/Digital/Edge-Detect-Circuitpng.png)

Verilog RTL 코드는 다음과 같다.

```verilog
module Edge_Detect(
    input           CLK,
    input           Signal,
    input           Reset_N,
    output      reg Falling_Edge_Detect,
    output      reg Rising_Edge_Detect,
    output      reg Both_Edge_Detect
);
    reg delay1, delay2;
    always @(posedge CLK, negedge Reset_N) begin
        if(~Reset_N) begin 
            delay1 <= 1'b0;
            delay2 <= 1'b0;
        end
        else begin 
            delay1 <= Signal;
            delay2 <= delay2;
            Falling_Edge_Detect = ~delay1 &  delay2;
            Rising_Edge_Detect  =  delay1 & ~delay2;
            Both_Edge_Detect    =  delay1 ^  delay2;
        end
    end
        
endmodule

```