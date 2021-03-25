https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ALDS1_11_B&lang=ja
![image](https://user-images.githubusercontent.com/46245101/112484659-7a973f80-8dbd-11eb-9270-15869b18c0ed.png)
![image](https://user-images.githubusercontent.com/46245101/112484679-808d2080-8dbd-11eb-995d-908911d55c3a.png)

ansをインクリメントするタイミングを迷った

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
vector<vector<ll>> V;
vector<ll> Map, A, B;
ll ans=0, inf=1<<30, cnt;

void dfs (ll prev, ll now, ll cnt) {
  ans++;
  A[now] = ans;
  Map[now] = cnt;
  for (auto i: V[now]) {
    if(Map[i]!=inf) continue;
    else {
      Map[i] = cnt;
      dfs(now, i, cnt);
    }
  }
  ans++;
  B[now]= ans;
}
 


int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n; cin >> n;
  V = vector<vector<ll>>(n, vector<ll>(0));
  Map = vector<ll>(n, inf);
  A = vector<ll>(n, 0);
  B = vector<ll>(n, 0);
  int u, k, v;
  REP(i, n) {
    cin >> u >> k;
    REP(j,k) {
      cin >> v;
      V[u-1].push_back(v-1);
    }
    sort(V[u-1].begin(), V[u-1].end());
  }

  // solve
  REP(i,n) if(Map[i]==inf) dfs(-1,i,0);
  // output
  REP(i, n) {
    cout << i+1 << ' ' << A[i] << ' ' << B[i] <<'\n';
  }
}
```
