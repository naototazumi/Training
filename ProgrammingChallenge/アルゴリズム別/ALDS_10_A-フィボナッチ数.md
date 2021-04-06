https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ALDS1_10_A&lang=ja

![image](https://user-images.githubusercontent.com/46245101/113718293-778a4080-9727-11eb-991c-d09f34ed301c.png)

```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
#define E 2.71828182845904523536
using namespace std;
using ll = long long;
vector<ll> DP;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n; cin >> n;
  DP = vector<ll>(n+1,0);
  DP[0] = 1;
  DP[1] = 1;
  REP3(i,2,n+1) {
    DP[i] = DP[i-1] + DP[i-2];
  }
  cout << DP[n] << '\n';

}
```
