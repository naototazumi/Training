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

  // input
  int n, x; cin >> n >> x;
  vector<ll> a(n);
  REP(i, n) {
    cin >> a[i];
  }

  // solve
  auto ans = solve(n, a);
  // output
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
c = gerchar(); //文字を1つずつ読み込み、改行も1文字
n = c - '0'; //数値に変換するには、文字コード番号の引き算をする
```


## DFS
```
vector<vector<int>> V;
vector<int> Map;
int ans=0, inf=1<<30;
 
void dfs (int prev, int now, int cnt) {
  for (auto i: V[now]) {
    if(Map[i]!=inf) continue;
    else {
      Map[i]=cnt;
      dfs(now, i, cnt);
    }
  }
}
 
  V = vector<vector<int>>(N, vector<int>(0));
  Map = vector<int>(N, inf);
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
