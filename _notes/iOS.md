---
title: "iOS 筆記"
---

## iOS Webview Interactions

Set Message Handler

```
let contentController = self.webView.configuration.userContentController
contentController.addScriptMessageHandler(self, name: "callbackHandler2")
```

<https://stackoverflow.com/a/38122947/737211>

iOS 下 javascript 與 Objective-C 互相調用
<https://www.jianshu.com/p/433e59c5a9eb>