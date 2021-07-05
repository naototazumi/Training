https://atcoder.jp/contests/abc095/tasks/arc096_a
![image](https://user-images.githubusercontent.com/46245101/124479704-7e395a00-dde1-11eb-8534-9cc7f1a983ed.png)


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

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll a, b, c, x, y, ans;
  cin >> a >> b >> c >> x >> y;
  ans = max(x, y)*2 * c;
  for(ll i=0; i <= max(x, y)*2 ;i+=2) {
    ans = min(ans, c*i + max((x-i/2)*a, ll(0)) + max((y-i/2)*b, ll(0))); 
  }

  cout << ans << '\n';
  //cout << setprecision(10) << ans << '\n';
}
```
