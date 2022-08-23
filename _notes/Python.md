---
title: "Python 筆記"
anchor: python-note
date : 01-01-2021
feed: show
---

## Python 2/3 切換

在 Windows 下如果需要在 Python 2/3 之間切換，可以用 `py` 指令:

同時安裝 Python 2 & 3
```
C:\Python27\
C:\Python33\
```

要跑 Python3 時:

    py -3 your_script.py

要跑 Python2 :

    py -2 your_script.py aurguments

## File IO

```
# open and write 
f = open("demofile2.txt", "w")
f.write("Now the file has more content!")
f.close()
```

```
# open and read the file:
f = open("demofile2.txt", "r")
print(f.read())
```

