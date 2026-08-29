---
title: 'TCP 三次握手：抓住抓包里的关键字段'
description: '用 Wireshark 视角复习 SYN / SYN-ACK / ACK，以及常见失败现象。'
pubDate: 'Aug 28 2026'
heroImage: '../../assets/blog-placeholder-2.jpg'
tags: ['网络工程', 'TCP/IP']
---

三次握手的目标很简单：**双方都确认「我能发、你也能收」**，并同步初始序列号。

## 过程概览

1. **客户端 → 服务端**：`SYN=1`，带上客户端初始序列号 `ISN_c`
2. **服务端 → 客户端**：`SYN=1, ACK=1`，带上服务端 `ISN_s`，确认号为 `ISN_c + 1`
3. **客户端 → 服务端**：`ACK=1`，确认号为 `ISN_s + 1`

握手完成后进入 Established，才开始传应用数据。

## 抓包时建议看这些

| 字段 | 看什么 |
| --- | --- |
| Flags | SYN / ACK 是否符合阶段预期 |
| Seq / Ack | 是否按 ISN+1 推进 |
| Window | 窗口是否异常为 0 |
| Options | MSS、SACK、Timestamp 是否协商成功 |

过滤示例：

```text
tcp.flags.syn == 1 or (tcp.flags.syn == 1 and tcp.flags.ack == 1)
```

## 常见异常

- **只有 SYN，没有 SYN-ACK**：对端未监听、防火墙丢弃、路由不通
- **反复重传 SYN**：RTT 大或丢包，看重传间隔是否指数退避
- **握手成功但立刻 RST**：应用层拒绝、安全策略或端口被抢占

下次实验可以刻意构造「对端端口未开」和「中途丢 SYN-ACK」，对照抓包加深印象。
