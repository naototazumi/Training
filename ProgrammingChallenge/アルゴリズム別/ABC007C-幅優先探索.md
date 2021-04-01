https://atcoder.jp/contests/abc007/tasks/abc007_3
![image](https://user-images.githubusercontent.com/46245101/113240886-8f596300-92e8-11eb-9545-9f3da1b9765b.png)

getchar()で上手く入力できずにはまった。stringを使うとすぐにできた。

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
ll r, c, sy, sx, gy, gx, inf=1<<30, cnt=0, y, x, nowy, nowx;
vector<vector<ll>> Map;
vector<ll> dy = {0,1,-1,0};
vector<ll> dx = {-1,0,0,1};

ll bfs(queue<pair<ll,ll>> q) {
  while(!q.empty()){
    pair<ll, ll> now;
    now = q.front(); q.pop();
    nowy = now.first; nowx= now.second;
    REP(i,4) {
      y = nowy+dy[i]; x = nowx+dx[i];
      if(y>=0 && y<r && x>=0 && x<c) {
        if(Map[y][x]==inf) {
          Map[y][x] = Map[nowy][nowx] + 1;
          q.push(make_pair(y, x));
        }
      }
    }
    if(Map[gy][gx]!=inf) return Map[gy][gx];
  }
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  // input
  cin >> r >> c >> sy >> sx >> gy >> gx;
  sy--; sx--; gy--; gx--;
  Map = vector<vector<ll>>(r, vector<ll>(c, -1));
  queue<pair<ll,ll>> q;
  string tmp;
  REP(i, r) {
    cin >> tmp;
    REP(j ,c) {
      if(tmp[j]=='.') Map[i][j] = inf;
      if(i==sy && j==sx) Map[sy][sx] = 0;
    }
  }
  REP(i,4) {
    y = sy+dy[i]; x = sx+dx[i];
    if(y>=0 && y<r && x>=0 && x<c) {
      if(Map[y][x]==inf) {
        Map[y][x] = 1;
        q.push(make_pair(y, x));
      }
    }
  }
  // solve
  auto ans = bfs(q);
  // output
  cout << ans << '\n';
}
```
