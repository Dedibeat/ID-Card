# ID-Card
branch 1 deer anhnii html bolon css ashiglan hiisen ID card baigaa ba main deer tuuniig lab6 iin hureend oorclon oruulsan 
Main deer bairlah Id card deer method POST iig ashiglasan baih ba ene ni servert utga ogc baigaag iltgene
harin method GET ashiglah ni SERVER deerees utga avch baigaa yavdal um Tiim ucraas ehleed Post hiihgui bol GET ashiglagdahgui bna
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define F first 
#define S second
using pt = pair<int, int>;
bool cmp(const pt &L, const pt &R)
{
    return (L.F * R.S - L.S * R.F) < 0;
}
bool cmp2(const pt &L, const pt &R)
{
    if(L.F < 0 && R.F >= 0) return 1;
    if(L.F >= 0 && R.F < 0) return 0;
    return cmp(L, R);
}
void solve()
{
    int n; cin >> n;
    vector<pair<int, int>> a(n);
    for(auto &[x, y] : a) cin >> x >> y;
    sort(a.begin(), a.end(), cmp2);
    //for(auto [x, y] : a) cout << ' ' << x << " " << y << endl;

    if(n < 3) 
    {
        cout << 0;
        return;
    }
    int ans = n;
    for(int i = 0; i < n; i++)
    {
        int l = 0, r = n;
        while(l + 1 < r)
        {
            int mid = (l + r) / 2;
            int idx = (i + mid) % n;
            pt A = {-a[i].F, -a[i].S};
            pt B = {a[idx].F - a[i].F, a[idx].S - a[i].S};
            //cout << "mid: " << mid << " " << idx << " ";
            int res = cmp2(A, B);
            // cout << "(" << A.F << " " << A.S << " " << B.F << " " << B.S << ")" <<endl;
            // cout << "cmp: " << res << endl;
            if(res) r = mid;
            else l = mid;
        }
        ans = min(ans,r - 1);

        // cout << "offset: " << r << endl;
        // cout << i << " to " << (i + r) % n << endl;
    }
    cout << ans;
}
signed main()
{
    int t; cin >> t; while(t--)
    {
        solve();
        cout << "\n";
    }
    
}
