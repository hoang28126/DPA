ĐỀ BÀI : https://www.spoj.com/PTIT/problems/SSAM219J/

Ý TƯỞNG : prefix sum + binery search

CODE : 
```sh
#include <bits/stdc++.h>
#define ll long long
using namespace std;

ll p[100001];
bool bns(int l, int r, ll s){
    while (l <= r){
        int m = (l + r) / 2;
        if (p[m] == s) return 1;
        if (p[m] > s) r = m - 1;
        if (p[m] < s) l = m + 1;
    }
    return 0;
}

int main(){
    int t; cin >> t;
    for(int j = 0; j < t; j++) {
        ll n, k; cin >> n >> k;
        memset(p, 0, sizeof(p));
        for(int i = 1; i <= n; i++){
            ll x; cin >> x;
            p[i] = p[i - 1] + x;
        }
        bool check = 0;
        for(int i = 1; i <= n; i++){
            if (p[i] >= k) {
                if (bns(0, i - 1, p[i] - k)) {
                    check = 1;
                    break;
                }
            }
        }
        if (check) cout << "YES";
        else cout << "NO";
        cout << endl;
    }
    
}
```
