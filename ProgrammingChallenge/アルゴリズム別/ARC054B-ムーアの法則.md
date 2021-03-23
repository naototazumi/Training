https://atcoder.jp/contests/arc054/tasks/arc054_b
![image](https://user-images.githubusercontent.com/46245101/112090237-88d73700-8bd6-11eb-93bf-443b940d04a4.png)
![image](https://user-images.githubusercontent.com/46245101/112090253-8f65ae80-8bd6-11eb-8414-6a524cbf3d1e.png)


解析的な解法：xが0未満となるようなpの範囲の計算を間違えた(p<=1.5/E/log(2) ⇒ p<=1.5/log(2))
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

  // input
  double p; cin >> p;
  if(p<=1.5/log(2)) cout<< setprecision(10) << p << '\n';
  else {
    double ans = 1.5/log(2)*(1-log(1.5/p/log(2)));
    cout << setprecision(10) << ans << '\n';
  }
}
```
