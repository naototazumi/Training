https://atcoder.jp/contests/practice

## 基本形
```
#include <bits/stdc++.h>
#define REP(i, n) for (ll i = 0; (i) < (ll)(n); ++ (i))
#define REP3(i, m, n) for (ll i = (m); (i) < (ll)(n); ++ (i))
#define REP_R(i, n) for (ll i = (ll)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (ll i = (ll)(n) - 1; (i) >= (ll)(m); -- (i))
#define E 2.71828182845904523536
#define F first 
#define S second 
#define PB push_back
#define MP make_pair
using namespace std;
using ll = long long;
using P = pair<ll,ll>;
vector<vector<ll>> G;
vector<ll> Map;
ll inf=1e18;
double Pi = 3.141592653589793;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll n, x; cin >> n >> x;
  vector<ll> a(n);
  REP(i, n) {
    cin >> a[i];
  }

  cout << setprecision(16) << fixed;
  cout << ans << '\n';
}
```

### ソート
```
##ベクトル昇順
sort(V.begin(), V.end())
// ベクトル降順
sort(V.begin(), V.end(), greater<int>())
```

### ループ
```
//bit全探索
for (int bit = 0; bit < (1<<n); bit++) { 
  for(int i = 0; i<n; i++) { 
    if(bit & (1<<i)) 

//ベクトルの全要素
for (auto i: V) {

//順列全探索
do {
  //...
} while(next_permutation(b.begin(),b.end()));

// setの全要素
  auto itr = s.begin();
  while (itr != s.end()) {
    // *itrでsetの要素を呼び出す
    itr++;
  }  
```

### ビットの1をカウント
```
__builtin_popcount(bit)
__builtin_popcountll(bit)
```

### データ型最大値
https://qiita.com/hryshtk/items/b848ed3bd78f940ac5af
```
short	32767
unsigned short	65535
int	2147483647
unsigned int	4294967295
long	9223372036854775807
unsigned long	18446744073709551615
long long	9223372036854775807
unsigned long long	18446744073709551615
```

## 二分探索(標準ライブラリ)
```
//初めてkey以上となるaの要素へのインデックスを返す(そのような要素がなければ最終インデックス+1を返す)
lower_bound(a.begin(),a.end(),key) - a.begin()
//初めてkeyより大きくなるaの要素へのインデックスを返す(そのような要素がなければ最終インデックス+1を返す)
upper_bound(a.begin(),a.end(),key) - a.begin()

//あるkeyより小さい要素の個数
lower_bound(a.begin(),a.end(),key) - a.begin()
//あるkey以上の要素の個数
a.end() - lower_bound(a.begin(),a.end(),key)
//あるkey以下の要素の個数
upper_bound(a.begin(),a.end(),key) - a.begin()
//あるkeyより大きい要素の個数
a.end() - upper_bound(a.begin(),a.end(),key)
```

## 二分探索(自力)
https://qiita.com/hamko/items/794a92c456164dcc04ad
```
  ll ng = s - 1, ok = t; //半開区間[s,t)の前提
  while (ok - ng > 1) {
    ll mid = (ng + ok) / 2;
    if(solve(mid)) ok = mid;
    else ng = mid;
  }
  if (ok == t) 
    cout << "for all x, solve(x) = false" << endl;
  else 
    cout << ok << endl;
```

## 三分探索：狭義凸関数(下に凸)の最小値を計算、3分の1ずつ区間を縮めていく。long doubleでないと収束しないケースがある
https://qiita.com/DaikiSuyama/items/84df26daad11cf7da453
```
long double solve(double n, double x) {
  return x+n*pow(2,-(x/1.5));
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  long double n; cin >> n;
  long double l=0.0, r=1e18, c1, c2;
  while(l+pow(10,-8)<r) {
    c1=l+(r-l)/3;
    c2=r-(r-l)/3;
    if (solve(n, c1) < solve(n, c2)) r=c2;
    else l=c1;
  }
  cout << setprecision(10) << solve(n, l) << '\n';
}
```

## 読み込み
```
//スペースで区切られた要素を読み込み、改行は無視
cin >> N; 

char c; int n;
c = getchar(); //文字を1つずつ読み込み、改行も1文字
n = c - '0'; //数値に変換するには、文字コード番号の引き算をする
```


## DFS
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
vector<ll> Map;
ll ans=0, inf=1<<30, cnt=0;

void dfs (ll prev, ll now, ll cnt) {
  Map[now] = cnt;
  cnt++;
  for (auto i: V[now]) {
    if(Map[i]!=inf) continue;
    else {
      dfs(now, i, cnt);
    }
  }
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll n; cin >> n;
  V = vector<vector<ll>>(n, vector<ll>(0));
  Map = vector<ll>(n, inf);
  ll x;
  REP(i, n) {
    cin >> x;
    V[i].push_back(x);
  }

  REP(i,n) if(Map[i]==inf) dfs(-1,i,cnt+1);
  // output
  cout << ans << '\n';
}
```

### BFS
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
### ナップザックDP
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
ll n, w;
vector<ll> Value, Weight;
vector<vector<ll>> DP;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  cin >> n >> w;
  Value = vector<ll>(n+1,0);
  Weight = vector<ll>(n+1,0);
  DP = vector<vector<ll>>(w+1, vector<ll>(n+1,0));
  REP3(i,1,n+1) cin >> Value[i] >> Weight[i];
  
  REP3(i,1,w+1) {
    REP3(j,1,n+1) {
      if(i>=Weight[j]) {
//各品物を1つしか選べない場合
//        DP[i][j] = max(DP[i][j-1], DP[i-Weight[j]][j-1]+Value[j]);
//各品物を複数個選べる場合
//        DP[i][j] = max(DP[i][j-1], max(DP[i-Weight[j]][j-1]+Value[j], DP[i-Weight[j]][j]+Value[j]));
      }
      else DP[i][j] = DP[i][j-1];
    }
  }
  cout << DP[w][n] << '\n';

}
```

### ダイクストラ法
ダイクストラ法は、行ける場所の中から「最も早く行ける場所」を順番に確定させていきます。
https://qiita.com/ageprocpp/items/cdf67e828e1b09316f6e#%E3%83%80%E3%82%A4%E3%82%AF%E3%82%B9%E3%83%88%E3%83%A9%E6%B3%95
https://algo-logic.info/dijkstra/
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
using P = pair<ll, ll>;
vector<vector<P>> edge;
vector<ll> dis, pre;
ll inf=1<<30;

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll v, e, r; cin >> v >> e >> r;
  edge = vector<vector<P>>(v);
  dis = vector<ll>(v, inf);
  pre = vector<ll>(v, -1);
  dis[r] = 0;
  ll s, t, d;
  REP(i, e) {
    cin >> s >> t >> d;
    edge[s].push_back(make_pair(d, t));
  }
  priority_queue<P, vector<P>, greater<P>> pq;
  //priority_queueの処理順カスタマイズ「要素の型、内部コンテナの型(デフォルトはvector)、昇順ならgreater<型(デフォルト降順)
  //pairで経路情報を保存、secondは行先の頂点、firstはその頂点へ行くための重み
  pq.push(make_pair(0,r));
  while(!pq.empty()) {
    P top = pq.top(); pq.pop();
    if(dis[top.second] < top.first) continue;
    //登録されている重みが、その頂点へ行くための重みより小さければ、この経路は無視
    else {
      for(auto i : edge[top.second]){
        if(dis[i.second] < top.first + i.first) continue;
        //行先に登録されている重みが、その頂点へ行くための重みより小さければ、この経路は無視
        else {
          dis[i.second] = top.first + i.first;
          pre[i.second] = top.second; 
          pq.push(make_pair(dis[i.second], i.second));
        }
      }
    }
  }
  REP(i, v){
    if(dis[i]==inf) cout << "INF";
    else cout << dis[i];
    cout << "\n";
  }
}
```

### ワーシャルフロイド法
全点対間最短経路で使う
https://qiita.com/saito_ry/items/55cb7473174df0be7621

```
  ll v, e, s, t, d; cin >> v >> e;
  vector<vector<ll>> dist(v, vector<ll>(v, inf));
  REP(i, e) {
    cin >> s >> t >> d;
    dist[s][t] = d;
  }
  REP(i, v) dist[i][i] = 0;
  
  REP(k, v) {
    REP(i, v) {
      if(dist[i][k]==inf) continue;
      REP(j, v) {
        if(dist[k][j]==inf) continue;
        dist[i][j] = min(dist[i][j], dist[i][k]+dist[k][j]);
      }
    }
  }
  bool flg = false;
  REP(i, v) if(dist[i][i]<0) {
    cout << "NEGATIVE CYCLE" << "\n";
    flg = true;
    break;
  }
  if(!flg) {
    REP(i, v) {
      REP(j, v) {
        if(dist[i][j]!=inf) cout << dist[i][j];
        else cout << "INF";
        if(j<v-1) cout << " ";
      }
      cout << "\n";
    }
  }
```
### 拡張ユークリッドの互除法、aとbの最大公約数gcd(a,b)を返し、ax+by=gcd(a,b)を満たすx,yも返す
```
ll ext_gcd(ll a, ll b,ll&x,ll&y) {
  if(b==0) {
    x=1; y=0;
    return a;
  }
  ll g = ext_gcd(b, a%b, x, y);
  ll z = x - (a/b)*y; 
  x=y;
  y=z;
  return g;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll a, b, x, y, g; cin >> a >> b;
  g = ext_gcd(a, b, x, y);
  
  cout << a << " " << b << " " << x << " " << y << "\n";
  cout << g << "\n";
}
```
```
ll modinv(ll a, ll m) {
  ll b = m, u = 1, v = 0;
  while (b) {
    ll t = a / b;
    a -= t * b; swap(a, b);
    u -= t * v; swap(u, v);
  }
  u %= m; 
  if (u < 0) u += m;
  return u;
}

int main() {
  // mod. 13 での逆元を求めてみる
  for (int i = 1; i < 13; ++i) {
    cout << i << " 's inv: " << modinv(i, 13) << endl;
  }
}
```

### 繰り返し二乗法
```
ll Pow(ll x, ll n) {
  ll ret = 1;
  while (n > 0) {
    if (n & 1) ret *=  x;  // n の最下位bitが 1 ならば x^(2^i) をかける
    x *=  x;
    n >>= 1;  // n を1bit 左にずらす
  }
  return ret;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll x, n; cin >> x >> n;
  cout << Pow(x, n) << "\n";
}
```
### 比較関数 pairのsecondの昇順、firstの降順
```
bool comp(pair<ll, ll> a, pair<ll, ll> b){
  if(a.second!= b.second) return a.second < b.second;
  else return a.first >= b.first;
}
```

### 階乗
```
ll factorial(ll k){
  ll sum = 1;
  REP3(i, 2, k+1) {
    sum *= i;
  }
  return sum;
}
```

### 素因数分解
```
vector<pair<ll, ll>> prime_factorize(ll N) {
  vector<pair<ll, ll> > res;
  for(ll a = 2; a*a <= N; a++) {
    if (N % a != 0) continue;
    ll ex = 0; // 指数
    // 割れる限り割り続ける
    while (N % a == 0) {
      ex++;
      N /= a;
    }
    // その結果を push
    res.push_back({a, ex});
  }
  // 最後に残った数について
  if (N != 1) res.push_back({N, 1});
  return res;
}

```

### 座標圧縮
https://algo-logic.info/coordinate-compress/
```
vector<ll> compress(vector<ll> &C) {
  vector<ll> vals; //圧縮前の座標候補を格納
  ll N = C.size();
  REP(i, N) {
    // その位置と、一つ隣を確保(隣を確保しないと空白が埋まってしまうことがある)
    REP(d, 1) {
      ll tc = C[i] + d;
      vals.push_back(tc);
    }
  }
  // ソート
  sort(vals.begin(), vals.end());
  // 隣り合う重複を削除(unique), 末端のゴミを削除(erase),eraseがないとREになる
  vals.erase(unique(vals.begin(), vals.end()), vals.end());
  // 圧縮前の座標候補の中で左から何番目なのかを二分探索で取得して座標を圧縮
  REP(i, N) C[i] = lower_bound(vals.begin(), vals.end(), C[i]) - vals.begin(); 
  return vals; //圧縮前の座標候補を返す。vals[圧縮後座標]で圧縮前座標を取り出せる。
}

//2つの配列をまとめて圧縮
vector<ll> compress(vector<ll> &a, vector<ll> &b) {
  vector<ll> vals; //圧縮前の座標候補を格納
  ll n = a.size();
  REP(i, n) {
    vals.PB(a[i]);
    vals.PB(b[i]);
  }
  // ソート
  sort(vals.begin(), vals.end());
  vals.erase(unique(vals.begin(), vals.end()), vals.end());
  // 圧縮前の座標候補の中で左から何番目なのかを二分探索で取得して座標を圧縮
  REP(i, n) {
    a[i] = lower_bound(vals.begin(), vals.end(), a[i]) - vals.begin(); 
    b[i] = lower_bound(vals.begin(), vals.end(), b[i]) - vals.begin(); 
  }
  return vals; //圧縮前の座標候補を返す。vals[圧縮後座標]で圧縮前座標を取り出せる。
}
```

### 組合せnCr 逆元
https://atcoder.jp/contests/abc145/submissions/27326116

### 組合せnCr パスカルの三角形
```
ll comb(ll n, ll r) {
  vector<vector<ll>> v(n+1,vector<ll>(n+1, 0));
  REP(i, n+1) {
    v[i][0] = 1;
    v[i][i] = 1;
  }
  REP3(i,1,n+1) REP3(j,1,i) v[i][j] = v[i-1][j-1]+v[i-1][j];
  return v[n][r];
}
```

### Union-Find
```
class UnionFind{
public:
  vector<ll> parent; //parent[i]はiの親
  vector<ll> siz; //素集合のサイズを表す配列(1で初期化)
  map<ll,vector<ll>> group; //集合ごとに管理する(key:集合の代表元、value:集合の要素の配列)
  ll n; //要素数

  //コンストラクタ
  UnionFind(ll n_):n(n_),parent(n_),siz(n_,1){ 
    //全ての要素の根が自身であるとして初期化
    for(ll i=0;i<n;i++){parent[i]=i;}
  }

  //データxの属する木の根を取得(経路圧縮も行う)
  ll root(ll x){
    if(parent[x]==x) return x;
    return parent[x]=root(parent[x]);//代入式の値は代入した変数の値なので、経路圧縮できる
  }

  //xとyの木を併合
  void unite(ll x,ll y){
    ll rx=root(x);//xの根
    ll ry=root(y);//yの根
    if(rx==ry) return;//同じ木にある時
    //小さい集合を大きい集合へと併合(ry→rxへ併合)
    if(siz[rx]<siz[ry]) swap(rx,ry);
    siz[rx]+=siz[ry];
    parent[ry]=rx;//xとyが同じ木にない時はyの根ryをxの根rxにつける
  }

  //xとyが属する木が同じかを判定
  bool same(ll x,ll y){
    ll rx=root(x);
    ll ry=root(y);
    return rx==ry;
  }

  //xの素集合のサイズを取得
  ll size(ll x){
    return siz[root(x)];
  }

  //素集合をそれぞれグループ化
  void grouping(){
    //経路圧縮を先に行う
    REP(i,n)root(i);
    //mapで管理する(デフォルト構築を利用)
    REP(i,n)group[parent[i]].PB(i);
  }

  //素集合系を削除して初期化
  void clear(){
    REP(i,n){parent[i]=i;}
    siz=vector<ll>(n,1);
    group.clear();
  }
};
```

### 最小全域木：Kruskal法
```
//以下、素集合と木は同じものを表す
class UnionFind{
public:
  vector<ll> parent; //parent[i]はiの親
  vector<ll> siz; //素集合のサイズを表す配列(1で初期化)
  map<ll,vector<ll>> group; //集合ごとに管理する(key:集合の代表元、value:集合の要素の配列)
  ll n; //要素数

  //コンストラクタ
  UnionFind(ll n_):n(n_),parent(n_),siz(n_,1){ 
    //全ての要素の根が自身であるとして初期化
    for(ll i=0;i<n;i++){parent[i]=i;}
  }

  //データxの属する木の根を取得(経路圧縮も行う)
  ll root(ll x){
    if(parent[x]==x) return x;
    return parent[x]=root(parent[x]);//代入式の値は代入した変数の値なので、経路圧縮できる
  }

  //xとyの木を併合
  void unite(ll x,ll y){
    ll rx=root(x);//xの根
    ll ry=root(y);//yの根
    if(rx==ry) return;//同じ木にある時
    //小さい集合を大きい集合へと併合(ry→rxへ併合)
    if(siz[rx]<siz[ry]) swap(rx,ry);
    siz[rx]+=siz[ry];
    parent[ry]=rx;//xとyが同じ木にない時はyの根ryをxの根rxにつける
  }

  //xとyが属する木が同じかを判定
  bool same(ll x,ll y){
    ll rx=root(x);
    ll ry=root(y);
    return rx==ry;
  }

  //xの素集合のサイズを取得
  ll size(ll x){
    return siz[root(x)];
  }

  //素集合をそれぞれグループ化
  void grouping(){
    //経路圧縮を先に行う
    REP(i,n)root(i);
    //mapで管理する(デフォルト構築を利用)
    REP(i,n)group[parent[i]].PB(i);
  }

  //素集合系を削除して初期化
  void clear(){
    REP(i,n){parent[i]=i;}
    siz=vector<ll>(n,1);
    group.clear();
  }
};

//辺の構造体
struct Edge{
  ll u,v,cost;
  //後ろにconstつける！
  bool operator<(const Edge& e) const {return this->cost<e.cost;}
};

//クラスカル法
//ret:=最小全域木の重みの総和
//n:=頂点の総数
//計算量:=O(m log{n})
ll Kruskal(vector<Edge> &edges,ll n){
  sort(edges.begin(), edges.end());//辺の重みの昇順
  UnionFind uf(n);
  ll ret=0;
  for(auto e:edges){
    //その辺を加える必要があるか
    if (!uf.same(e.u,e.v)){
      uf.unite(e.u,e.v);
      ret+=e.cost;
    }
  }
  return ret;
}


int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';
  
  ll n, m, x, y, c, ans;
  cin >> n >> m;
  vector<Edge> edges;
  Edge e;
  REP(i, m) {
    cin >> x >> y >> c;
    e.u=x;
    e.v=y;
    e.cost=c;
    edges.PB(e);
  }
  sort(edges.begin(), edges.end());
  ans = Kruskal(edges, n);
  cout << ans << '\n';
}
```


### その他マクロ
```
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
#define rep(i, n) for(int i = 0; i < (n); i++)
#define rep1(i, n) for(int i = 1; i <= (n); i++)
#define co(x) cout << (x) << "\n"
#define cosp(x) cout << (x) << " "
#define ce(x) cerr << (x) << "\n"
#define cesp(x) cerr << (x) << " "
#define getchar getchar_unlocked
#define putchar putchar_unlocked
#define pb push_back
#define mp make_pair
```


//整数の各桁の数字を合計する
int SumOfDigits(int n) {
  int sum = 0;
  while (n > 0) { 
    sum += n % 10;
    n /= 10;
  }
  return sum;
}

//int型の入力を受け取る
int getint() {
    char C; int s = 0, t = 1;
    while (!isdigit(C = getchar())) if(C=='-') t=-1;
    do {s = s * 10 + C - '0'; } while( isdigit(C = getchar()));
    return s * t;
}  

//delete a factor in vector
V.erase(V.begin()+i);  
