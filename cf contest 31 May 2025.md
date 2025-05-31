/***************************  
https://codeforces.com/contest/2116/problem/B  
***************************/  
#include <bits/stdc++.h>
using namespace std;

#define tourist int main(){ios::sync_with_stdio(0);cin.tie(0);  // tourist - fast input output
#define Ace_Azimuth_Aviator return 0;}                          // Ace_Azimuth_Aviator - return 0;

#define pss <<' '                                               // pss - print single space
#define lss if(i!=n-1)cout<<' ';                                // lss - !(last single space)
#define pnl cout<<'\n';                                         // pnl - print new line
#define tcl int t;cin>>t;while(t--){                            // tcl - test case loop
#define tnl if(t)pnl}                                           // tnl - testcase new line

#define pye cout<<"YES";                                        // pye - print YES
#define pno cout<<"NO";                                         // pno - print NO
#define pyn ?cout<<"YES":cout<<"NO";                            // pyn - print YES/NO
#define pny ?cout<<"NO":cout<<"YES";                            // pny - print NO/YES

#define bat bool ans=true;                                      // bat - boolean answer true
#define baf bool ans=false;                                     // baf - boolean answer false
#define atb {ans=true;break;}                                   // atb - answer true break
#define afb {ans=false;break;}                                  // afb - answer false break

#define lli long long                                           // lli - long long
#define imx INT_MAX;                                            // imx - INT_MAX
#define imn INT_MIN;                                            // imn - INT_MIN
#define con const int c=1e9                                     // con - constant
#define mod %1'000'000'007                                      // mod - modular

#define aii vector<int>a(n);for(auto&x:a)cin>>x;                // aii - a-vector int input
#define ali vector<lli>a(n);for(auto&x:a)cin>>x;                // ali - a-vector long long input
#define bii vector<int>b(n);for(auto&x:b)cin>>x;                // bii - b-vector int input
#define bli vector<lli>b(n);for(auto&x:b)cin>>x;                // bli - b-vector long long input

#define all(a) a.begin(),a.end()                                // all(a) - all elements of the container a
#define rall(a) a.rbegin(),a.rend()                             // rall(a) - all elements of the container a in reverse order
#define allc(a) a.cbegin(), a.cend()                            // allc(a) - all elements of the const container a
#define rallc(a) a.crbegin(), a.crend()                         // rallc(a) - all elements of the const container a in reverse order

#define pub(a,x) a.push_back(x)                                 // pub(a,x) - push back x in container a
#define emb(a,x) a.emplace_back(x)                              // emb(a,x) - emplace back x in container a

#define noz find(all(a),0)==a.end()                             // noz - no zero exists in the vector
#define dbz [&](){for(int i=1;i<n;++i)\
if(!a[i]&&!a[i-1])return 1;return 0;}()                         // dbz - double zero exists in the vector
#define l2c(x) (int)ceil(log2(x))                               // l2c(x) - log2(x) rounded up

#define gnp goto print;                                         // gnp - go n print
#define pnt print:cout<<                                        // pnt - print

const lli md = 998244353;

lli getval(const lli& e) {
    lli result = 1, base = 2 % md, exp = e;
    while (exp > 0) {
        if (exp % 2 == 1)result = (result * base) % md;
        base = (base * base) % md, exp /= 2;
    }
    return result;
}

tourist tcl
lli n; cin >> n; ali bli

vector<pair<lli, lli>>mxa(n), mxb(n);
for (lli i = 0, mxval = -1, mxidx = -1; i < n; ++i) {
    if (a[i] > mxval)mxval = a[i], mxidx = i;
    mxa[i] = { mxval,mxidx };
}

for (lli i = 0, mxval = -1, mxidx = -1; i < n; ++i) {
    if (b[i] > mxval)mxval = b[i], mxidx = i;
    mxb[i] = { mxval,mxidx };
}

for (lli i = 0; i < n; ++i)cout << max(getval(mxa[i].first) + getval(b[i - mxa[i].second]), getval(mxb[i].first) + getval(a[i - mxb[i].second]))pss;
tnl Ace_Azimuth_Aviator
