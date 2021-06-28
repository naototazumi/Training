https://atcoder.jp/contests/abc122/tasks/abc122_b
![image](https://user-images.githubusercontent.com/46245101/123646993-aca7ba00-d862-11eb-9836-75ca8a76bf02.png)

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
 
  string s; cin >> s;
  ll ans=0, cnt=0;
  REP(i, size(s)) {
    if(s[i]=='A'||s[i]=='C'||s[i]=='G'||s[i]=='T') cnt++;
    else {ans = max(ans, cnt); cnt=0;}
  }
  cout << max(ans, cnt) << '\n';
}
```

最後の文字列がACGTだった時にansとcntの最大を取ることを漏らした
