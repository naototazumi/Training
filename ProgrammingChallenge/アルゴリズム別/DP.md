# 典型的な DP (動的計画法) のパターンを整理
https://qiita.com/drken/items/a5e6fe22863b7992efdb

## ナップザック問題
https://judge.u-aizu.ac.jp/onlinejudge/submission.jsp#submit/DPL_1_B
![image](https://user-images.githubusercontent.com/46245101/111132446-b57ac580-85bc-11eb-9b55-62069408dc77.png)


```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
using namespace std;
using ll = long long;


int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n, w; cin >> n >> w;
  vector<int> V(n, 0), W(n,0);
  vector<vector<int>> dp(n+1, vector<int>(w+1,0));
  REP(i, n) {
    cin >> V[i] >> W[i];
  }

  // solve
  REP(i,n) {
    REP3(j,1,w+1){ //ここをwにしてハマった
      if(j>=W[i]){
        dp[i+1][j]= max(dp[i][j], dp[i][j-W[i]]+V[i]);
      }
      else dp[i+1][j]= dp[i][j];
    }
  }

  // output
  cout << dp[n][w] << '\n';
}
```
