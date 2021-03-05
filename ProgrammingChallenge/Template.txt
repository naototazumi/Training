//main
#include<bits/stdc++.h>
using namespace std;
int main() {
  long long ans=0;
  int N; cin >> N;
  for (int i=0; i<N; i++) {
    
  }
  cout << ans << "\n";
}


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



#include<bits/stdc++.h>
using namespace std;
int main() {
    cin.tie(0);
    ios::sync_with_stdio(false);

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

//bit全探索
for (int bit = 0; bit < (1<<n); bit++) { 
  for(int i = 0; i<n; i++) { 
    if(bit & (1<<i)) 

//for loop
for (int i=0; i<N; i++)

//sort
sort(V.begin(), V.end(), greater<int>())


import sys
sys.setrecursionlimit(1000000)

//iterate for each factor of vector
for (auto i: V) {

//delete a factor in vector
V.erase(V.begin()+i);  

__builtin_popcount(bit)
__builtin_popcountll(bit)
