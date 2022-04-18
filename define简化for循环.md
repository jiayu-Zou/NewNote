使用宏定义：

```c++
#define _for(i,a,b) for(int i=(a); i<(b); ++i)
#define _rep(i,a,b) for(int i=(a); i<=(b); ++i)

_for(i, 0, 3){
    cout << i << endl;
} // 这里可以不用提前声明i 
```

