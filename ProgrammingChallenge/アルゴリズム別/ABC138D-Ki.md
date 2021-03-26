https://atcoder.jp/contests/abc138/tasks/abc138_d
![image](https://user-images.githubusercontent.com/46245101/112593560-04411e80-8e4b-11eb-9eba-4b4467135162.png)
![image](https://user-images.githubusercontent.com/46245101/112593582-0b682c80-8e4b-11eb-8548-e610e2e66f8f.png)


aとbで、必ずしもaが根に近いとは限らないことを見落としていた<br>
直線でも根でも、上流に与えた数字は必ず下流に流れていくことを利用。上流側から、前の要素の値を今の要素に加算することを逐次的に繰り返せば、線形時間で解ける。

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
vector<ll> Map, Ans, Q;
ll ans=0, inf=1<<30, cnt=0;

void dfs (ll prev, ll now) {
  Map[now]=0;
  if(prev>0) Ans[now] += Ans[prev];
  for (auto i: V[now]) if(Map[i]==inf) dfs(now, i);
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll n, q; cin >> n >> q;
  V = vector<vector<ll>>(n+1,vector<ll>(0));
  ll a, b;
  REP(i, n-1) {
    cin >> a >> b;
    V[a].push_back(b);
    V[b].push_back(a);
  }
  Ans = vector<ll>(n+1,0);
  REP(i, q) {
    cin >> a >> b;
    Ans[a] += b;
  }
  Map = vector<ll>(n+1, inf);
  dfs(-1, 1);
  // output
  REP3(i,1,n) cout << Ans[i] << ' ';
  cout << Ans[n] << endl;
}
```
![image](https://user-images.githubusercontent.com/46245101/112593836-6c900000-8e4b-11eb-9fd7-8e91bb56b498.png)
