https://atcoder.jp/contests/abc023/tasks/abc023_d
![image](https://user-images.githubusercontent.com/46245101/111947999-c8901700-8b21-11eb-864b-f38c7fa5a537.png)
![image](https://user-images.githubusercontent.com/46245101/111948013-d04fbb80-8b21-11eb-8b52-6b751ee92c2b.png)


```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
using namespace std;
using ll = long long;

bool solve(int n, ll mid, const vector<pair<ll,ll>>& a) {
  vector<ll> b(0);
  REP(i,n) {
    if(mid < a[i].first) return false;
    else {
      b.push_back((mid-a[i].first)/a[i].second);
    }
  }
  sort(b.begin(),b.end());
  REP(i,n) if(b[i]<i) return false;
  return true;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n; cin >> n;
  vector<pair<ll,ll>> a(n);
  ll x, minstart= 1e18, maxend=0;
  REP(i, n) {
    cin >> a[i].first >> a[i].second;
    minstart = min(minstart,a[i].first);
    maxend = max(maxend,ll(a[i].first + a[i].second*(n-1)));
  }

  // solve
  ll ng = minstart - 1, ok = maxend+1; //半開区間[s,t)の前提
  while (ok - ng > 1) {
    ll mid = (ng + ok) / 2;
    if(solve(n, mid, a)) ok = mid;
    else ng = mid;
  }
  if (ok == maxend+1) 
    cout << "for all x, solve(x) = false" << endl;
  else 
    cout << ok << endl;
}
```
