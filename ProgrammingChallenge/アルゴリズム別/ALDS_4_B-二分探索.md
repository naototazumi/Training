https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ALDS1_4_B&lang=ja

ポイント：setの二分探索：set.lower_bound()
setはイテレータを返してくる：`*`をつけることで参照先の値を取得できる


```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
using namespace std;
using ll = long long;

ll solve(int q, const set<int>& a, const vector<int>& b) {
  int tmp=0, x;
  REP(i,q){
    if(*a.lower_bound(b[i]) == b[i]) tmp++;
  }
  return tmp;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  int n, x; cin >> n;
  set<int> a;
  REP(i, n) {
    cin >> x;
    a.insert(x);
  }
  int q; cin >> q;
  vector<int> b(q);
  REP(i, q) cin >> b[i];
  // solve
  auto ans = solve(q,a,b);
  // output
  cout << ans << '\n';
  //cout << setprecision(10) << ans << '\n';
}
```
