https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=DPL_1_C&lang=ja
![image](https://user-images.githubusercontent.com/46245101/113880310-57758280-97f6-11eb-9ad1-3381b018a47d.png)
![image](https://user-images.githubusercontent.com/46245101/113880337-5f352700-97f6-11eb-9183-949a94bb9134.png)

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
ll n, w;
vector<ll> Value, Weight;
vector<vector<ll>> DP;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  cin >> n >> w;
  Value = vector<ll>(n+1,0);
  Weight = vector<ll>(n+1,0);
  DP = vector<vector<ll>>(w+1, vector<ll>(n+1,0));
  REP3(i,1,n+1) cin >> Value[i] >> Weight[i];
  
  REP3(i,1,w+1) {
    REP3(j,1,n+1) {
      if(i>=Weight[j]) {
        DP[i][j] = max(DP[i][j-1], max(DP[i-Weight[j]][j-1]+Value[j], DP[i-Weight[j]][j]+Value[j]));
      }
      else DP[i][j] = DP[i][j-1];
    }
  }
  cout << DP[w][n] << '\n';

}
```
