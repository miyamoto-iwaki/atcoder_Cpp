# 標準ライブラリを使う方法
## gccの場合
```cpp
#include <bits/stdc++.h>
using namespace std;
```
## その他の環境(Visual Studio 2019など)
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
```
***
## 絶対値 abs
`abs(x) = (x の絶対値)`となる。`cmath`をインクルードすることにより使える。

## 三角関数 sin/cos/tan
`x`は度数法ではなく弧度法を用いることに注意。`cmath`をインクルードすることにより使える。
```cpp
double pi = 3.141592653589793238;
double x;
cin >> x;

// 小数点以下10桁まで出力される
cout << fixed << setprecision(10);

//x度の時の値を出力
cout << sin(x / 180.0 * pi) << endl;
cout << cos(x / 180.0 * pi) << endl;
cout << tan(x / 180.0 * pi) << endl;
```
