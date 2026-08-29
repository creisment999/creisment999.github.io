---
title: 'Running network commands with Python subprocess'
description: 'Wrap ping / traceroute in a script for batch probing and logging.'
pubDate: 'Aug 27 2026'
heroImage: '../../assets/blog-placeholder-4.jpg'
tags: ['programming', 'Python', 'automation']
---

Network labs often mean typing the same commands again and again. Putting them in a script makes parameters and logs easier to manage.

## Minimal example

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

## Notes

- On Windows, `ping` uses `-n`; on Linux/macOS it uses `-c`
- Prefer an argument list over `shell=True` with a concatenated string — safer against injection
- In production probes, add `timeout=` and a concurrency limit so you do not overload the network

Next step: read a host list → ping in parallel → write CSV, as a small health-check tool.
