
TortoiseGit 跟 Dropbox 圖示衝突

打開 `regedit`，到下面這個位置

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers
```

然後修改順序，Dropbox 非常無恥的用兩個空格占用最前面的位置。

Dropbox 保留 01 (in sync), 02 (in progress), 05 (sync error), 07 (grey not syncing)