# 標準ライブラリを使う方法
## gccの場合
```cpp
#include <bits/stdc++.h>
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
| S.substr(i , j)       | Sの i 文字目から i+j-1 文字目までの部分文字列を返す       |

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
vector<int> c = { 1, 2, 3, 4, 5 };
int minx = 2147483647;

// 例 1： 配列 c の最小値を出力する方法 1 つ目
for (int i = 0; i < c.size(); i++) minx = min(minx, c.at(i));
cout << minx << endl;

// 例 2: 配列 c の最小値を出力する方法 2 つ目
cout << *min_element(c.begin() , c.end()) << endl;
```
## 値の交換 swap
`swap(a, b)` で、変数 a と b の値を入れ替えることができる。

## 最大公約数 __gcd
2 つの整数 a, b の最大公約数を返す関数。
`__gcd(a,b) = (a と b の最大公約数)`となる。計算量は$` O(\log a) `$のため高速。`algorithm` をインクルードすることで使える。

なお、a, bの最小公倍数は`__gcd(a,b) * b`によって求まる
> [!CAUTION]
> **この関数は gcc で利用可能だが、Visual Studio 2019 などでは使えない。**

関数が使えない場合のgcdの関数を以下に記す。
```cpp
int gcd(int a, int b) // a > b
{
  if(b == 0) return a;
  return gcd(b, a % b);
}
```

## 配列の合計 reduce
`int`や`double`の配列の合計値算出に対応する。`reduce(配列変数.begin(),配列変数.end())`で配列の合計値を返す。
```cpp
vector<int> c = { 1, 2, 3, 4, 5 };

// 配列cの合計を求める
cout << reduce(c.begin(), c.end()) << endl;
```

## 配列を逆順に並び替え reverse
配列 c のある区間を逆順に並び替える。

| プログラム | 説明 | 
|:-----------|:------------|
| reverse(c.begin(), c.end())      | cを逆順にすべて並び替える   | 
| reverse(c.begin() + i, c.begin() + j)    | c の i 番目から j 番目までを逆順に並び替える    | 

```cpp
vector<int> b = {8, 3, 7, 1, 4, 6, 2, 5};

// 例 1: 配列 a の 1～6 番目の要素を逆順にします。{8, 6, 4, 1, 7, 3, 2, 5} に変化します。
reverse(b.begin() + 1, b.end() -2);
for (int i = 0; i < b.size(); i++) cout << b[i] << " ";
cout << endl;
```

## ソート sort
`reverse(c.begin(), c.end())`によって配列を小さい順に並び変える。文字列は辞書順に並び替える。C++の順序では`'0'`～`'9'`→`'A'`～`'Z'`→`'a'`～`'z'`である。`algorithm` をインクルードすることで使える。計算量は$` O(N\log N) `$。
```cpp
// 配列cを小さい順に並び替える。c = {1, 2, 3, 4, 5, 6, 7, 8} となる
vector<int> c = {8, 3, 7, 1, 4, 6, 2, 5};
sort(c.begin(), c.end());
for (int i = 0; i < c.size(); i++) cout << c[i] << " ";
cout << endl;

// 配列sを辞書順に並び替える。c = {"America", "Canada", "France", "Japan"} となる
vector<string> s = {"Japan","Canada","France","America"};
sort(s.begin(), s.end());
for (int i = 0; i < s.size(); i++) cout << s[i] << " ";
cout << endl;
```

## 配列 vector
`vector`は動的な配列を表す型。以下 a を`vector`型の変数、x を適当な変数または値とする。

| プログラム | 説明 | 
|:-----------|:------------|
| a.push_back(x)      | a の末尾に x を追加   | 
| a.pop_back(x)    | a の末尾の要素を除去    |
| a.size()    | a の要素数を返す    |

計算量は$` O(1) `$と高速。

## 型変換 to_string、stoi、stoll、stod
以下、文字列は`char`ではなく`string`である。
| プログラム | 説明 | 
|:-----------|:------------|
| to_string(x)      | 数値型から文字列に変換し、文字列を返す  | 
| stoi(x)    | 文字列から`int`に変換し、`int`を返す    |
| stoll()    | 文字列から`int64_t`に変換し、`int64_t`を返す   |
| stod(a)    | 文字列から`double`に変換し、`double`を返す   |

## 要素の個数 count
配列や`vector`のある区間の要素の中で、x がいくつ含まれるかを返す関数。
`count(v.begin(), v.end(), x)` によって配列 v の中で x となるようなものの個数を返す。

## 順列全探索 next_premutation
以下、vectorの配列vに対する「順列全探索」の雛形。なお、事前に`sort`が必要なことに注意。
```cpp
sort(v.begin(), v.end());
do {
  // 順列に対する処理
} while (next_permutation(v.begin(), v.end()));
```

# 「値」以上[を超える]の最小の値 lower_bound[upper_bound]





