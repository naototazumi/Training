## 基本形
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

ll solve(int n, const vector<ll>& a) {
  ll tmp=0;
  // ...
  return tmp;
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  ll n, x; cin >> n >> x;
  vector<ll> a(n);
  REP(i, n) {
    cin >> a[i];
  }

  auto ans = solve(n, a);
  cout << ans << '\n';
  //cout << setprecision(10) << ans << '\n';
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

## 三分探索：狭義凸関数(下に凸)の最小値を計算、3分の1ずつ区間を縮めていく
https://qiita.com/DaikiSuyama/items/84df26daad11cf7da453
```
double solve(double n, double x) {
  return x+n*pow(2,-(x/1.5));
}

int main() {
  ios::sync_with_stdio(false);
  cin.tie(nullptr);
  constexpr char endl = '\n';

  double n; cin >> n;
  double l=0.0, r=1e18, c1, c2;
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
