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
# 以下覚えておくべき標準ライブラリ
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

## 文字列 string
以下、S, T を `string` 型の変数、c を `char` 型の変数とする。

| プログラム | 説明 | 
|:-----------|:------------|
| S[i]       | Sのi文字目。`char`型であることに注意   | 
| S += T (or c)     | `string`や`char`を連結可能      | 
| S.size()      | Sの長さを整数型で返す        |
| S.substr(i)         | Sの i 文字目から最後の文字までの部分文字列を返す          |
| S.substr(i,j)       | Sの i 文字目から i+j-1 文字目までの部分文字列を返す       |

## 最小値・最大値 min/max
複数の値の、最小値・最大値を返す関数。以下、c は適当な型の配列。

| プログラム | 説明 |
|:-----------|:------------|
| min(a,b)       | 2 つの値 a, b のうち小さい方を返す        |
| max(a,b)    | 2 つの値 a, b のうち大きい方を返す    |
|  min({a1, a2, ..., an})      | {a1, a2, ..., an} の中で最小のものを返す        |
| max({a1, a2, ..., an})     |{a1, a2, ..., an} の中で最大のものを返す  |
| *min_element(c + l, c + r)       | {c[l], c[l+1], ..., c[r-1]} の中で最小のものを返す |
| *max_element(c + l, c + r)    | {c[l], c[l+1], ..., c[r-1]} の中で最大のものを返す|

なお、`min_element` 関数と `max_element` 関数はイテレーターを返すため、最初に * を付ける必要がある。`algorithm` をインクルードすることで使える。
```cpp
// 例2： {c[1], c[2], ..., c[N]} の最小値を出力する方法 1 つ目
int N, c[100009], minx = 2147483647;
cin >> N;
for (int i = 1; i <= N; i++) cin >> c[i];
for (int i = 1; i <= N; i++) minx = min(minx, c[i]);
cout << minx << endl;

// 例 2: {c[1], c[2], ..., c[N]} の最小値を出力する方法 2 つ目
cout << *min_element(c + 1, c + N + 1) << endl;
```
## 値の交換 swap
`swap(a, b)` で、変数 a と b の値を入れ替えることができる。

## 最大公約数 __gcd
2 つの整数 a, b の最大公約数を返す関数。
> [!CAUTION]
> この関数は gcc で利用可能だが、Visual Studio 2019 などでは使えない。
