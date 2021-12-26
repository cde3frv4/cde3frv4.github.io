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
## <u>Write Leveling 동작 개요</u>



### **1.MR1명령**  
 \- **MR1.A7=1** 로 Write Leveling 모드 활성화 (DESELECT 명령만 허용)  
 \- MR1.A12메모리 컨트롤러는 Rank당 Write Leveling 동작 
    → <span style="color:blue">동작 Rank는 MR1.A12=1, 미동작 Rank는 MR1.A12=1</span>
  


|기능                      |MR1 |Enable  |Disable  
|----                      |--- |---    |--- 
|WriteLeveling             |A7  |1      |0
|Output buffer mode (Qoff) |A12 |0      |1 

### **2.MR1.A7=1 설정**  
 (1) tLDQSEN: ODT 기능 사용 시 다음을 만족해야 함  
 \- tWLDQSEN > tMOD(Min) + ODTLon + tADC: at DLL = Enable  
 \- tWLDQSEN > tMOD(Min) + tAONAS: at DLL = Disable    
 (2) tDQSL : DQS_t Low

<center><img src="/assets\images\DDR4\WriteLeveling\WriteLeveling-1.png" width="100%"  title="" alt="WriteLeveling-Entry"/>
<figcaption>WriteLeveling-Entry</figcaption></center>



 Because the controller levels one rank at a time,
the output of other ranks must be disabled by setting MR1 bit A12 to 1. The controller
may assert ODT after tMOD, at which time the DRAM is ready to accept the ODT signal,
unless DODTLon or DODTLoff have been altered (the ODT internal pipe delay is increased
when increasing WRITE latency [WL] or READ latency [RL] by the previous MR
command), then ODT assertion should be delayed by DODTLon after tMOD is satisfied,
which means the delay is now tMOD + DODTLon.
The controller may drive DQS_t LOW and DQS_c HIGH after a delay of tWLDQSEN, at
which time the DRAM has applied ODT to these signals. After tDQSL and tWLMRD, the
controller provides a single DQS_t, DQS_c edge, which is used by the DRAM to sample
CK driven from the controller. tWLMRD (MAX) timing is controller dependent.
The DRAM samples CK status with the rising edge of DQS and provides feedback on all
the DQ bits asynchronously after tWLO timing. There is a DQ output uncertainty of
tWLOE defined to allow mismatch on DQ bits. The tWLOE period is defined from the
transition of the earliest DQ bit to the corresponding transition of the latest DQ bit.
There are no read strobes (DQS_t, DQS_c) needed for these DQs. The controller samples
incoming DQ and either increments or decrements DQS delay setting and launches
the next DQS pulse after some time, which is controller dependent. After a 0-to-1
transition is detected, the controller locks the DQS delay setting, and write leveling is
achieved for the device. The following figure shows the timing diagram and parameters
for the overall write leveling procedure.



```
<center><img src="/assets\images\DDR4\hPPR-MR0GuardKeys.jpg" width="90%" height="90%" title="가드키 스펙" alt="아무거나"/></center>


## <u>hPPR  - Hard Fail Row Address Repair (WRA Case)</u>
**1. PRE(PreCharge)**<br>
 \- 모든 Bank는 Precharge가 되어야 함, DBI 및 CGC 모드 Off<br><br>
**2. MR4.A[13]=1 설정 -> tMOD**<br>
\- Enable hPPR 후 tMOD 대기<br><br>
**3. MR0.A[17:0] guard Key  4회 설정**<br>
\- 각각의  MR0 명령 사이에  tMOD 시간 대기<br><br>
**4. ACT(Active) -> tRCD**<br>
\- Fail Row 주소와 함께 Active 후 tRCD 대기<br><br>
<center><img src="/assets\images\DDR4\hPPR-Entry.jpg" width="90%" height="90%" title="" alt=""/></center>
<br><br><br>

**5. WRA(Write with Auto Precharge)**   
\- 유효주소와 함께 WRA 인가, 실제 WRA와 유효주소를 'Don't Care 처리(Addressing/Write처리 안함)<br><br> 
**6.tPGM 대기 :  WL(WL=CWL+AL+PL) + 4tCK + 기타 시간 포함**  
\- 4tCK동안 DQ는 모두 0 이어야 함  
\- tPGM(x4, x8 : min 1000ms, x16 : min 2000ms)동안 DRAM Row Repair 기다림<br><br>
**7.PRE(PreCharge) -> tPGM_Exit**  
\- Precharge 후 tPGM_Exit 시간동안 Repair된 주소 DRAM 내부 인식<br><br>
**8.MR4.A[13]=0 설정 -> tPGM_PST**  
\- hPPR Mode Disable 후 tPGM_PST 시간 후, 다른 명령 진입 가능
<center><img src="/assets\images\DDR4\hPPR-Repair.jpg" width="90%" height="90%" title="" alt=""/></center>
```
