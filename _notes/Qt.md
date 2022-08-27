---
title: Qt
feed: show
---


### Q: 什麼是 Widget ?
A widget is a visual element in a user interface.

### Q: 什麼是 signal/slot ?

signal/slot 是 Qt 的事件觸發機制，白話理解就是建立一個連結：一旦甲事件發生後，就去做乙事。比如收到貨款後(signal)就寄出貨物(slot)。按下按鈕後(signal)，就彈出一個視窗(slot)，。

建立 signal/slot 的方式是透過呼叫 `QObject::connect()`，通常長這樣:

    QObject::connect ( 元件一, SIGNAL(事件), 元件二, SLOT(事件) );

因為大部分的Qt class都繼承自QObject，所以也可以直接在物件裡面呼叫connect()

signal 表示目前物件發生了某些變化，而slot 則是接受到訊息之後的工作。


#### 如何移除signal/slot的連接?

    QObject::disconnect()


#### signal/slot 可以自由配對，是多對多的關係。

一個 singal 可以送給很多個slot。<br>
一個 slot 也可以接收很多個signal。<br>
一個singal也可以連接到另一個singal，如果多個 signal 串在一起會連鎖觸發。


### Layout 的用法

通常是先製造一個 Layout 出來，然後把元件加進去。

```
QXXLayout * layout = new QXXLayout;
layout->addWidget( w1 );
layout->addWidget( w2 );
```

最後再把這個layout 用setLayout() 加進母容器裡。

    mother->setLayout(layout);

### 如果想要修改 UI 的值，但是不想發送 signal 怎麼辦?

直接呼叫 widget->blocksignals( true ); 改完再設 widget->blocksignals( false );
或者用 QSignalBlocker ，在離開 scope 之後把狀態設回來。


###  Qt的繼承架構:

幾乎所有的物件都繼承QObject ，有繼承的才能用signal/slot。

QObject 下面物件體系分為三支: 
第一個是QApplication ，這是Qt的核心，裡面有主事件迴圈。
第二個是QWidget，這是所有可視元件的根。
第三個是QLayout，這是所有排版元件的根。

### Qt UI Loader

QUiLoader 可以在runtime 才載入 .ui 檔，就像這樣

```cpp
QUiLoader uiLoader;
QWidget * w = uiLoader.load(QFile("kerker.ui"));
if( w ) { ... }
```

Note: 要使用 QUiLoader 要加一行 CONFIG += uitools

### Qt Creator的快速鍵

Ctrl + Shift + R = 重構命名
F4 切換標頭檔與實作檔 .h .cpp 
F2 是跳到定義式 (查詢源頭)
F1 跳出Help, Reference

### Qt Event

Qt 事件處是使用冒泡事件機制，也就是裡面的小元件會先收到event，是由子元件開始，一層層由內往外傳的，最外面的大元件最後收到事件。

一個元件要收鍵盤事件，必須要先拿到Focus。

    this->setFocus( );

如果打算就攔截此事件，就呼叫 `event->accept()`
如果打算讓事件繼續往外傳，就呼叫 `event->ignore()`

### Designer plugin 

關於新增designer plugins
http://doc.qt.nokia.com/qtcreator-snapshot/adding-plugins.html

The integrated Qt Designer  fetches plugins from the %SDK%\bin\designer folder on Windows and Linux.

擴充(繼承) Qt Widget 又要維持拖拉功能
http://developer.qt.nokia.com/doc/qt-4.8/designer-using-custom-widgets.html

### Disable qDebug() outputs

想要移除所有的qDebug()輸出，只要在.pro文件裡加上一行
DEFINES += QT_NO_DEBUG_OUTPUT

### QGraphicsView 簡介

http://kheresy.wordpress.com/2011/07/30/customize_qgraphicsitem/


### 產生 Visual Studio Project ( *.vcxproj / *.sln) 的指令

    qmake -tp vc

### 產生 Xcode project 的指令

    qmake -spec macx-xcode the_project.pro

### 該怎麼打開使用者的"我的文件"目錄?

    QStandardPaths::writableLocation(QStandardPaths::DocumentsLocation);

### 要怎麼獲取一個檔案的相關資訊?

QFileInfo
http://blog.sina.com.cn/s/blog_3e62c50d01013xd4.html

- Qt 的檔案處裡
- Qt 的字串處理
- Qt 的繪圖機制

```cpp
#define UIBlockSignal(UI) QSignalBlocker SCOPEGUARD_LINENAME(myBlocker, __LINE__)  ((UI));
```

### Qt 本地化

需要的工具:

1. lupdate
2. lrelease

### TLS initialization failed 

    qt.network.ssl: QSslSocket::connectToHostEncrypted: TLS initialization failed

First, check the OpenSSL version your Qt built with

    qDebug() << "ssl:" << QSslSocket::sslLibraryBuildVersionString();

Download the corresponding version of OpenSSL

<http://slproweb.com/products/Win32OpenSSL.html>

Copy the DLL files to your exe folder (or system32)

Qt source code for loading OpenSSL dlls

<https://code.woboq.org/qt5/qtbase/src/network/ssl/qsslsocket_openssl_symbols.cpp.html>


### QTreeView 

Simple Tree Model Example:

<https://doc.qt.io/qt-5/qtwidgets-itemviews-simpletreemodel-example.html>
