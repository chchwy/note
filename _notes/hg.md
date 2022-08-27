---
title: Hg
feed: show
---

Mercurial (hg) 是一個比較小眾的版本管理系統。

這裡備忘一些簡單的 hg 操作指令

克隆遠端倉庫

```shell
hg clone https://the-repo-url
```

列出所有遠端倉庫位址 (類似 git remote)

    hg paths

拉下遠端倉庫更新

    hg pull
    hg update // 要做這行才會更新 working copy

捨棄本地修改

    hg revert the-path/to-file

顯示倉庫狀態

    hg sum    // summary 的簡寫
    hg status

列出所有分支

    hg branches

建立新分支

    hg branch <feature_branch>

切換分支

    hg update your-branch

推送 PR 常用

    hg push chchwy --branch my-fix-branch --new-branch

