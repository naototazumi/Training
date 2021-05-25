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
試し割法：計算量が O(√N) 
```
C++
using ll = long long;
vector<ll> prime_factorize(ll n) {
  vector<ll> res;
  if  (n % 2 == 0) {
    while (n % 2 == 0) {
      res.push_back(2);
      n /= 2;
    }      
  }
  for (ll a = 3; a * a <= n; a+=2) {
    if (n % a != 0) continue;
    while (n % a == 0) {
      res.push_back(a);
      n /= a;
    }
  }
  if (n != 1) res.push_back(n);
  sort(res.begin(), res.end());
  return res;
}

Python
def prime_factorize(n):
    a = []
    while n % 2 == 0:
        a.append(2)
        n //= 2
    f = 3
    while f * f <= n:
        if n % f == 0:
            a.append(f)
            n //= f
        else:
            f += 2
    if n != 1:
        a.append(n)
    return a
```

# エラトステネスの篩

```
C++
using ll = long long;
vector<ll> sieve(ll n) {
  vector<bool> is_prime(n, true);
  is_prime[0] = false;
  REP3(i,2,n+1){
    if(is_prime[i-1]) {
      ll j = 2 * i;
      while(j <= n) {
        is_prime[j-1] = false;
        j += i;
      }
    }
  }
  vector<ll> table;
  REP3(i, 1, n+1) if(is_prime[i-1]) table.push_back(i); 
  return table;
}


Python
def sieve(n):
    is_prime = [True for _ in range(n+1)]
    is_prime[0] = False

    for i in range(2, n+1):
        if is_prime[i-1]:
            j = 2 * i
            while j <= n:
                is_prime[j-1] = False
                j += i
    table = [ i for i in range(1, n+1) if is_prime[i-1]]
    return is_prime, table
```

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
