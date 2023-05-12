---
author: Kaushik Chemburkar
pubDatetime: 2023-05-12T19:42:00+11:00
title: Recursively delete 'node_modules' folders
postSlug: recursive-delete
featured: false
draft: false
tags:
  - terminal
  - macos
ogImage: ""
description:
  A terminal command to delete all 'node_modules' or any other folders recursively.
---

As I am using a 256GB hard-drive, I often need to free up space. I have many projects on my computer, and each project has a `node_modules` folder. These folders can take up a lot of space, so I often delete them. However, I don't want to go through each project and delete the `node_modules` folder manually. So I [found a terminal command on stackoverdlow](https://stackoverflow.com/questions/42950501/delete-node-modules-folder-recursively-from-a-specified-path-using-command-line) to do it for me.

```bash
find /path/to/start -name "node_modules" -type d -prune -exec rm -rf {} +
```

## Explanation

`find`: This is the command that searches for files in a directory hierarchy

`/path/to/start`: This is the directory you want to start searching from. Replace this with your actual starting directory

`-name "node_modules"`: This tells `find` to search for directories with the name "node_modules"

`-type d`: This tells `find` to only search for directories (not files)

`-prune`: This prevents find from descending into the current file. This is needed because if `find` descends into the directory before deleting it, it can cause errors.

`-exec rm -rf {} +`: This tells `find` to execute the `rm -rf` command (which deletes directories) on each directory it finds. The `{}` is replaced by the current file name.
