## 基本形
```
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; (i) < (int)(n); ++ (i))
#define REP3(i, m, n) for (int i = (m); (i) < (int)(n); ++ (i))
#define REP_R(i, n) for (int i = (int)(n) - 1; (i) >= 0; -- (i))
#define REP3R(i, m, n) for (int i = (int)(n) - 1; (i) >= (int)(m); -- (i))
#define ALL(x) std::begin(x), std::end(x)
using namespace std;
using ll = long long;

ll solve(int n, const vector<ll>& a) {
  int tmp=0;
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

## 読み込み
```
//スペースで区切られた要素を読み込み、改行は無視
cin >> N; 

char c; int n;
c = gerchar(); //文字を1つずつ読み込み、改行も1文字
n = c - '0'; //数値に変換するには、文字コード番号の引き算をする
```


//DFS
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

//double変数を15ケタ表示
cout<<fixed<<setprecision(15)<<ans<<"\n";

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




