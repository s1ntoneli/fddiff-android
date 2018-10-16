# fddiff-android

辅助定位 fd 泄露的工具。
检查 android 应用 fd, 展示两次应用操作之间的 fd 变化情况。

    -p, --pkg       package name
    -v              verbose

## 用法:

    fddiff -p com.android.browser -v
    fddiff -p com.android.browser

## 结果:

	- 当前 fd 数量
	- 新增 fd 数量及明细
	- 释放的 fd 数量及明细


## 示例:

```
$ fddiff -p com.android.browser
Fds file init finished.

$ fddiff -p com.android.browser
total: 190
New fds: 0
Freed fds: 0

$ fddiff -p com.android.browser
total: 195
New fds: 7
Freed fds: 2

$ ./fddiff -p com.android.browser -v
New fds: 8
lrwx------ 1 u0_a184 u0_a184 64 186 -> socket:[142571]
lrwx------ 1 u0_a184 u0_a184 64 191 -> socket:[140304]
lrwx------ 1 u0_a184 u0_a184 64 193 -> socket:[140928]
lr-x------ 1 u0_a184 u0_a184 64 102 -> anon_inode:sync_file
lr-x------ 1 u0_a184 u0_a184 64 132 -> pipe:[142570]
lr-x------ 1 u0_a184 u0_a184 64 197 -> pipe:[142577]
l-wx------ 1 u0_a184 u0_a184 64 196 -> pipe:[142570]
l-wx------ 1 u0_a184 u0_a184 64 198 -> pipe:[142577]

Freed fds: 6
lrwx------ 1 u0_a184 u0_a184 64 102 -> socket:[140668]
lrwx------ 1 u0_a184 u0_a184 64 132 -> socket:[141580]
lrwx------ 1 u0_a184 u0_a184 64 173 -> socket:[140675]
lrwx------ 1 u0_a184 u0_a184 64 186 -> socket:[140304]
lrwx------ 1 u0_a184 u0_a184 64 72 -> socket:[132855]
lr-x------ 1 u0_a184 u0_a184 64 191 -> anon_inode:sync_file

total: 197
New fds: 8
Freed fds: 6

```
