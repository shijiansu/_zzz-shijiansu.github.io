---
date: 2021-09-26
author: Su Shijian
title: "MTTR"
tags: ["Terminologies - M"]
categories: ["Site Reliability Engineering", "Reliability"]
description: >
---

> MTTR (Mean Time to Restoration, 平均恢复前时间), 源自于IEC 61508中的平均维护时间 (Mean Time to Repair), 目的是为了清楚界定术语中的时间的概念, MTTR是随机变量恢复时间的期望值. 它包括确认失效发生所必需的时间, 以及维护所需要的时间. MTTR也必须包含获得配件的时间, 维修团队的响应时间, 记录所有任务的时间, 还有将设备重新投入使用的时间.
>
> MTTR也必须包含获得配件的时间, 维修团队的响应时间, 记录所有任务的时间, 还有将设备重新投入使用的时间.
>
> 有些系统有内置冗余, 所以, 当一个子系统出现故障, 另一国的地位, 保持整个系统的运行. 虽然整体系统具有零MTTR, 故障子系统仍然需要修理或更换, 因此子系统只有一个非零MTTR.

- https://www.uniquelims.net/xinwen/hyxw/155.html
- Date: Unknown
