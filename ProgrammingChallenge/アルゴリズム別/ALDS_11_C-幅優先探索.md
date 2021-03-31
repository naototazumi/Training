https://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ALDS1_11_C&lang=ja
![image](https://user-images.githubusercontent.com/46245101/113087736-396cb880-921f-11eb-919d-8ddec08d00b5.png)



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

  int n; cin >> n;
  vector<vector<ll>> A(n+1,vector<ll>(0));
  ll u, v, w;
  queue<pair<ll,ll>> q;
  vector<ll> Map(n+1, -1);
  Map[1] = 0;

  REP(i, n) {
    cin >> u >> v;
    REP(j, v){
      cin >> w;
      A[u].push_back(w);
      if(u==1) {
        q.push(make_pair(w,1));
        Map[w] = 1; 
      }
    }
  }
  
  pair<ll, ll> r;
  while(!q.empty()){
    r = q.front() ;
    q.pop();
    for(auto s: A[r.first]){
      if(Map[s]==-1) {
        Map[s]=r.second + 1;
        q.push(make_pair(s, Map[s]));
      }
    }
  }
  
  REP3(i,1,n+1) cout << i << ' ' << Map[i] << endl;

}
```
