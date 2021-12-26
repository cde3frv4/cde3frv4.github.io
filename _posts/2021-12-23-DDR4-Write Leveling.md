---
layout: single
title: "DDR4 - WriteLeveling"
categories: DDR4
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
classes: wide

#published: false
---

## <u>Write Leveling 개요</u>

## <u>Write Leveling 동작 순서</u>

### **1.MR1명령**

 \- <span style="color:blue">MR1.A7=1</span> 로 Write Leveling 모드 활성화 (DESELECT 명령만 허용)  
 \- MR1.A12메모리 컨트롤러는 Rank당 Write Leveling 동작 
    → <span style="color:blue">동작 Rank는 MR1.A12=1, 미동작 Rank는 MR1.A12=1</span>

| 기능                        | MR1 | Enable | Disable |
|:-------------------------:|:---:|:------:|:-------:|
| WriteLeveling             | A7  | 1      | 0       |
| Output buffer mode (Qoff) | A12 | 0      | 1       |

### **2. tWLMRD (tLDQSEN+1DQSL)**

 (1) tLDQSEN: ODT 기능 사용 시 다음을 만족해야 함  
  \- tWLDQSEN > tMOD(Min) + ODTLon + tADC: at DLL = Enable  
  \- tWLDQSEN > tMOD(Min) + tAONAS: at DLL = Disable    
 (2) tDQSL : DQS_t Low

### **3. tDQSH – tWLO – tWLOE**

 \- DRAM은 DQS_t - DQS_c의 상승 에지로 CK_t - CK_c 상태를 샘플링하고, 모든 DQ 비트에 대한 피드백을 비동기식으로 제공한다. DQS Rising edge에서 CLK이 “0” 이면 DQ에 “0”을 , CLK이 “1”이면 DQ에 “1”을 출력한다. 

 (1) tWLO   : Rising edge에서 샘플링한 CK의 피드백이 DQ로 나오는 시점

 (2) tWLOE :  가장 빨리 전송되는 DQ bit와 늦게 전송되는  DQ bit 시간차

<center><img src="/assets\images\DDR4\WriteLeveling\WriteLevelingSequence.png" width="100%"  title="" alt="WriteLeveling-Entry"/>
<figcaption>WriteLeveling-Entry</figcaption></center>
