https://atcoder.jp/contests/abc077/tasks/arc084_a
![image](https://user-images.githubusercontent.com/46245101/111928031-d6c83e00-8af5-11eb-8032-e9cfbad8eb7f.png)
![image](https://user-images.githubusercontent.com/46245101/111928058-ec3d6800-8af5-11eb-8d22-299be191e3ec.png)

ポイント：Aより大きいBに対して、それより大きいCを探す方法だとTLEになった。<br>
Bの各要素に対して、それより小さいＡの個数とそれより大きいＣの個数を求め、掛け合わせる方法だと行けた
解答がintだと収まらないことがあり、llにする必要があった。

```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
using namespace std;
using ll = long long;

ll solve(int n, const vector<ll>& d, const vector<ll>& e) {
  ll tmp=0;
  REP(i,n) tmp += d[i]*e[i];
  return tmp;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n; cin >> n;
  vector<ll> a(n),b(n),c(n);
  REP(i, n) cin >> a[i];
  sort(a.begin(),a.end());
  REP(i, n) cin >> b[i];
  sort(b.begin(),b.end());
  REP(i, n) cin >> c[i];
  sort(c.begin(),c.end());

  vector<ll> d(n), e(n);
  REP(i,n) {
    d[i] = lower_bound(a.begin(),a.end(),b[i])-a.begin(); //bの各要素より小さいaの要素の数
    e[i] = c.end() - upper_bound(c.begin(),c.end(),b[i]); //bの各要素より大きいcの要素の数
  }
  // solve
  auto ans = solve(n, d, e);
  // output
  cout << ans << '\n';
}
```
