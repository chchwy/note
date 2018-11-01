---
title: "ClayGL 筆記"
anchor: claygl
---

`fbx2gltf.py` 使用方法

### 安裝 Fbx python 

https://www.autodesk.com/products/fbx/overview

預設安裝位置
C:\Program Files\Autodesk\FBX\FBX Python SDK\2018.1.1\lib

### 安裝 python

一定要安裝跟 FBX sdk 對應的版本。
以 Python fbx 2018.1.1 為例，到以下目錄看：
C:\Program Files\Autodesk\FBX\FBX Python SDK\2018.1.1\lib

會發現這個 SDK 版本提供了 2.7 跟 3.3 的函式庫。那就你的 Python 就一定要是 2.7.x/3.3.x，不要安裝其他版本。
我安裝了最新的 Python 3.7 就發現不相容。

### 複製 py/pyd

複製以下目錄裡的 py/pyd 
C:\Program Files\Autodesk\FBX\FBX Python SDK\2018.1.1\lib\Python33_x86

到以下目錄
C:\Python33\Lib\site-packages


