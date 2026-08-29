---
title: '用 Python 跑网络命令：subprocess 最小示例'
description: '把 ping / traceroute 包进脚本，方便批量探测和记日志。'
pubDate: 'Aug 27 2026'
heroImage: '../../assets/blog-placeholder-4.jpg'
tags: ['编程', 'Python', '自动化']
---

网络实验里经常要重复敲命令。把命令放进脚本，方便改参数、留日志。

## 最小例子

```python
import subprocess
from datetime import datetime

def ping_host(host: str, count: int = 4) -> str:
    result = subprocess.run(
        ['ping', '-c', str(count), host],
        capture_output=True,
        text=True,
        check=False,
    )
    stamp = datetime.now().isoformat(timespec='seconds')
    return f'[{stamp}] exit={result.returncode}\n{result.stdout}{result.stderr}'

if __name__ == '__main__':
    print(ping_host('8.8.8.8'))
```

## 使用注意

- Windows 上 `ping` 的参数是 `-n`，Linux/macOS 是 `-c`
- 不要用字符串拼命令再 `shell=True`，优先传参数列表，减少注入风险
- 生产环境探测建议加超时（`timeout=`）和并发上限，避免把自己打挂

下一步可以做成「读主机列表 → 并行 ping → 输出 CSV」，当作小型巡检工具。
