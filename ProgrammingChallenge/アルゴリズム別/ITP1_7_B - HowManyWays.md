https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_7_B&lang=ja

![image](https://user-images.githubusercontent.com/46245101/114876326-2e2da580-9e39-11eb-86b0-ee49c79ea289.png)


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

  ll n, x, ans;
  while(true){
    ans=0; cin >> n >> x;
    if(n==0 && x==0) break;
    REP3(i, 1, n-1) {
      REP3(j, i+1, n){
        if(x-i-j>j && x-i-j<=n) ans++;
      }
    }
    cout << ans << "\n";
  }
}
```



計算範囲を以下の通り誤った、0以上n未満ではなく、1以上n以下。
```
REP(i, n-2) {
  REP3(j, i+1, n-1){
```
