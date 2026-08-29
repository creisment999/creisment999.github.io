---
title: 'TCP three-way handshake: fields that matter in a capture'
description: 'Review SYN / SYN-ACK / ACK from a Wireshark perspective, plus common failure modes.'
pubDate: 'Aug 28 2026'
heroImage: '../../assets/blog-placeholder-2.jpg'
tags: ['networking', 'TCP/IP']
---

The three-way handshake has a simple goal: **both sides confirm they can send and receive**, and they synchronize initial sequence numbers.

## Overview

1. **Client → server**: `SYN=1`, with client ISN `ISN_c`
2. **Server → client**: `SYN=1, ACK=1`, with server ISN `ISN_s`, ack = `ISN_c + 1`
3. **Client → server**: `ACK=1`, ack = `ISN_s + 1`

After this, the connection is Established and application data can flow.

## What to check in a capture

| Field | What to look for |
| --- | --- |
| Flags | SYN / ACK match the expected stage |
| Seq / Ack | Advance as ISN+1 |
| Window | Not stuck at 0 unexpectedly |
| Options | MSS, SACK, Timestamp negotiated as expected |

Filter example:

```text
tcp.flags.syn == 1 or (tcp.flags.syn == 1 and tcp.flags.ack == 1)
```

## Common failures

- **SYN only, no SYN-ACK**: peer not listening, firewall drop, or routing issue
- **Repeated SYN retransmits**: loss or high RTT; check exponential backoff
- **Handshake OK, then RST**: app rejected the connection, security policy, or port conflict

A useful lab: force “port closed” and “dropped SYN-ACK” cases, then compare captures.
