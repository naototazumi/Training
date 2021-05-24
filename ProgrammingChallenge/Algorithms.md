https://qiita.com/H20/items/1a066e242815961cd043

# 除算の切り上げ、切り下げ
C++：正の整数を正の整数で割った場合、答えは必ず切り捨てになる。
Python：切り捨て除算//は除算値を超えない最大の整数
```
C++
# 整数A,BについてA/Bの切り捨てを求める書き方
F = A / B
# 整数A,BについてA/Bの切り上げを求める書き方
C = (A + B - 1) / B

Python
# 整数A,BについてA/Bの切り捨てを求める書き方
F = A // B
# 整数A,BについてA/Bの切り上げを求める書き方
C = -(-A // B)
```


# 約数列挙
計算量が O(√N) となるため、制約のNが10^12までなど大きな値をとる場合にはまず約数を疑ってかかるのも手。

```
C++
using ll = long long;
vector<ll> divisors(ll n) {
  vector<ll> ret;
  for (ll i = 1; i * i <= n; i++) {
    if (n % i == 0) {
      ret.push_back(i);
      if (i * i != n) ret.push_back(n / i);
    }
  }
  sort(ret.begin(), ret.end()); // 昇順に並べる
  return ret;
}

Python
def make_divisors(n):
  lower_divisors , upper_divisors = [], []
  i = 1
  while i*i <= n:
    if n % i == 0:
      lower_divisors.append(i)
      if i != n // i:
        upper_divisors.append(n//i)
    i += 1
  return lower_divisors + upper_divisors[::-1]
```


# 素因数分解

# エラトステネスの篩

# BIT全探索

# Union-Find

# クラスカル法（最小全域木）

# リスト（配列）の中身を連結・結合して文字列に

# 多次元配列のソート

# defaultdict（辞書）

# カウンター

# ModInt

# 逆元

# 階乗

# コンビネーション

# ある値の累乗の何度も使用する場合

# 最大公約数

# 中国剰余定理

# DFS

# 二分探索（bisect）

# 二分探索（その他）

# 最長増加部分列（LIS）

# 累積和（合わせて、いもす法）

# 短めな順列の作成

# 二次元累積和

# ダイクストラ法

# ワーシャルフロイド法

# セグメント木（セグ木）

# 転倒数

# 桁DP

# ダブリング

# 最長共通部分列

# BitDP

# 10進数を2進数、8進数、16進数に変換

# 10進数とn進数の変換

# 正規表現

# キュー

# 優先度付きキュー

# しゃくとり法
