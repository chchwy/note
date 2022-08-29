
### Item 1:  視 C++ 為語言聯邦

一些自己的重點筆記，條款 1~4 試圖傳達一些 [[C++]] 常識：

C++具有四種語言典範

- C語言
- 物件導向OO
- Generics (Template)
- STL

### Item 2:  以 const , eum, inline 取代 define

這則應該是常識了，原因就在於 C++ 的編譯流程中，前處理(preprocessing)和編譯(compiler)是兩個獨立的步驟。
當前處理棄置換 #define 符號時，編譯器是完全不知情的。編譯器拿到的是置換完畢後的源碼，因此產生的錯誤訊息也比較不精確。
所以盡可能讓前處理器(preprocessor)退役，使用原生的 compiler 功能。

### Item 3: 盡可能使用 const

探討了 const, mutable 關鍵字的用法
探討了 bitwise const, logical const 的意義
避免 const, non-const 兩種版本的函數內容重複

### Item 4: 確定物件使用前已經被初始化

跟 C語言相容的部份，通常要自己初始化
C++的部份則是盡量都作到宣告就初始化

> !! 注意: 危險的 non-local static 物件，初始化順序無法確定

這幾個條款是要人熟悉C++底下偷幹的好事
- constructor
- destructor
- copy constructor
- assignment operator

### Item 5: 了解C++默默編寫並調用了哪些函數

```
class Doctor
{
    std::string& myName; // member 是 reference
};

Doctor d1, d2;
d1 = d2; // copy!!!
```

在這個狀況下，C++會拒絕為你產生 default copy assignment 因為他不知道該怎麼處理 reference。C++不允許 reference被重新榜定。

### Item 6: 明確拒絕編譯器自動生成的函數

使用 explicit

### Item 7: 為多態類別宣告 virtual dtor

常識了

### Item 8: 別讓異常跳脫析構函數

兩次異常的下場就是程式終止，

### Item 9: 絕不在ctor/dtor呼叫 virtual function

跟建構/解構的順序有關，在 ctor 階段，子類別可能還沒有初始化，這時候的 virtual function  可能不會執行正確工作。

### Item 10: 令 operator= 回傳 *this

小技巧讓 class 更加像原生型別

### Item 11: 在 operator= 處裡自我賦值

小技巧讓 `operator=` 不要不小心釋放掉不該放的資源

### Item 12: 在複製物件時勿忘其每一個成份

常識

### Item 13 以物件管理資源 (RAII)

這幾個條款在討論資源分派跟釋放的問題。
C++是典型要求程序員手動處裡資源的語言，所以這部份也是重中之重

重點有二

- 取得資源之後立刻放進管理物件(ex. shared_ptr)
- 利用管理物件的dtor來釋放資源
- 書裡使用 auto_ptr 來做示範 (目前C++11已經廢棄)
- 但是要小心不要用二個以上的 smart_ptr 來管理同一個資源物件。

### Item 14 在資源管理類裡面小心 Copying 行為

這樣到底會發生什麼事?
解法一：禁止複製
解法二：底部使用引用計數 (reference count)

```
Lock m11(&m);
Lock m12(&m11); // 將m11複製到m12身上
```

### Item 15 在資源管理類中提供原始資源訪問

廢話...

### Item 16  用相同形式成對使用 new/delete

​廢話...

### Item 17 以獨立語句將newed物件置入智能指針

非常罕見的case, 典型搞死自己的類型。
​
```cpp
void processWidget(std::shared_ptr<Widget> pw, int priority); // 宣告
processWidget(new Widget, priority());                        // 實際呼叫
```

實際上有可能很作死，先 new 物件，然後跑 priority() 接著拋出 exception，然後 Widget 還來不及被 shared_ptr 接住，函數就離開了。
