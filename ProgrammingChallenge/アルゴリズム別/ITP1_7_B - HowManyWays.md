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

ll solve(int n, int x) {
  ll tmp=0;
  REP3(i,1,n-1){
    REP3(j,i+1,n){
      REP3(k,j+1,n+1){
        if(i+j+k==x) tmp++;
      }
    }
  }
  return tmp;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';
 
  int n, x;
  while(true){
    cin >> n >> x;
    if(n==0 && x==0) break;
    auto ans = solve(n, x);
    cout << ans << '\n';
  }
}
```
