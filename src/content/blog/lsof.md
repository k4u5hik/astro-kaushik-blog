---
author: Kaushik Chemburkar
pubDatetime: 2023-05-09T16:49:00+11:00
title: Useful lsof commands
postSlug: lsof
featured: false
draft: false
tags:
  - lsof
  - terminal
  - macos
  - linux
ogImage: ""
description:
  Useful lsof commands
---

1. View the top 10 processes with the most open files on your system.

    ```bash
    lsof -n | awk '{print $1}' | sort | uniq -c | sort -nr | head -10
    ```

2. List all open TCP and UDP ports and their associated processes

    ```bash
    lsof -i | grep -E "(LISTEN|UDP)" | awk '{print $1, $9}' | sort | uniq
    ```

3. List all listening ports and their associated process names

    ```bash
    lsof -i -P -n | grep LISTEN | awk '{print $9, $1}' | sort | uniq
    ```

4. Find all open files larger than a specific size, such as 100MB, and sort by size

    ```bash
    lsof -s | awk '$7 > 100*1024*1024 {print $7, $1, $2, $9}' | sort -nr
    ```

5. Count the number of open files per process, sorted by process name
  
    ```bash
    lsof -n | cut -f1 -d' ' | sort | uniq -c | sort -k2,2
    ```
