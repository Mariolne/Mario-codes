# Mario-codes 
ACM algorithm
//https://www.luogu.com.cn/problem/P1219
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl '\n'
const int N = 19;
int t[N];
bool col[N] , dg[2*N] , udg[2*N];
int n,ans = 0;
void dfs(int u){
    if(u > n) {
        ans++;
        if(ans <= 3){
        for(int i = 1 ;i <= n ;i++) cout<<t[i]<<" ";
        cout<<endl;
        }
        return;
    }
    for(int i = 1 ; i <=n ;i++){
        if(!col[i] && !dg[u+i] && !udg[n-u+i]){
            col[i] = dg[u+i] = udg[n-u+i] = true,t[u] = i;
            dfs(u+1);
            col[i] = dg[u+i] = udg[n-u+i] = false,t[u] = 0;
        }
    }
}
void solve(){
    cin>>n;
    dfs(1);
    cout<<ans;
    
}
signed main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t = 1;
    //cin >> t;
    while (t--) {
        solve();
    }
    return 0;
}
