---
layout: single
title: "DDR4 - Refresh"
categories: ddr4
tag: [ddr4]
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
classes: wide

#published: false
---

## <u>Refresh Mode와 Truth Table</u>

-tRFC와 tREFI 는 MRS 명령에 의해 프로그램된다. 

## <u>Refresh Command Flexibility</u>

Refresh는 어느정도의 **유연성 있는 동작을 제공한다.** 그림을 보면 알 수 있다.  
일반적인 환경에서는 Refresh는 일정 주기(tREF)로 동작한다. 그리고 Refresh 동작 중(tRFC)에는 다른 명령어가 들어오지 못한다. Refresh 동작 중에는 다른 명령어가 들어올 수 없다.

<center><img src="/assets\images\DDR4\Refresh\Refresh Command Timing.png" width="100%" title="" alt="Refresh_Timing"/></center>

.

<center><img src="/assets\images\DDR4\Refresh\Refresh2-PostponingRefresh.png" width="90%" title="" alt="Refresh_Postponing"/></center>

위 그림은 1XPostponing Refresh 동작이다. 최대 8개의 Refresh 명령이 나중에 실행될 수 있고, 사전에 최대 9*tREFI 까지 최대 명령 간격을 늘릴 수 있다

<center><img src="/assets\images\DDR4\Refresh\Refresh2-PulllingRefresh.png" width="90%" title="" alt="Refresh_Pulling"/></center>

위 그림은 1XPulling Refresh 동작이다. 최대 8개의 Refresh 명령을 미리 실행되게 하여, 나중에 최대 9*tREFI 까지 최대 명령 간격을 늘릴 수 있다.

마찬가지로  2X, 4X Refresh 모드를 쓰면 각각 16, 32 Refresh 명령을 한번에 실행 가능하고, 해당 명령의 수만큼 최대 17\*tREFI2와   33*tREFI4의 최대시간을 확보할 수 있다.
