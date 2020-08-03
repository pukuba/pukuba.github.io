---
title: atcoder ABC174 풀이
layout: post
tags: AtCoder ABC
categories: PS

date: 2020-07-27 03:31:00
--- 

# AtCoder Beginner Contest 174 풀이

###  **URL** 
* https://atcoder.jp/contests/abc174

### **A - Air Conditioner**

X를 입력받고 X가 30 이상이면 "Yes" 그렇지않는다면 "No"를 출력 합니다.

### **B - Distance**

N,D를 입력받고 N번 X,Y를 입력받을때 sqrt(pow(X,2) + pow(Y,2)) 가 D 이하면 정답을 1증가합니다.

### **C - Repsept**


타카하시가 좋아하는 수는 7이며 7,77,777,7777,...? 꼴의 수를 좋아합니다.

K를 입력받고 K의 배수가 타카하시가 좋아하는 수가 되는 시점이 몇 번째의 타카하시가 좋아하는 수인지 출력해야 합니다.

우선 K가 2의 배수, 5의 배수인 경우에는 답이 나오지 않아 -1을 출력합니다.

그 이유는 2n과 5n의 마지막 자릿수는 7로 끝날 수 없기 때문입니다.

타카하시가 좋아하는 수마다 K로 나누어보고 나누어떨어지면 그때의 Count를 출력합니다.
```c++
while(here){
    here = here*10+7;
    here %= K;
    cnt++;
}
```

### **D - Alter Altar**

입력받은 문자열에서 R 왼쪽에 W가 있으면 안 됩니다. 문자열에서 2문자의 위치를 서로
변경할 수 있고 한 문자의 색을 변경할 수 있습니다. 문자열을 최소한 몇 번 건드리면 올바른
문자열을 만들 수 있는지 출력하면 되는 문제입니다.

문자열에서 R이 나오는 index를 모아두고 R이 나오는 횟수를 구합니다. 

이후 R의 개수보다 Ri 번째의 index가 작거나 같으면 움직일 필요가 없다는 뜻이기 때문에 count
를 하나 올리고 R개수에서 count를 뺀 것이 답이 됩니다.

``` c++
#include <bits/stdc++.h>

using namespace std;
int n,cnt;
string s;
vector<int> v;
int main(){
    ios_base::sync_with_stdio(0);cin.tie(nullptr);
    cin>>n>>s;
    for(int i=0; i<s.size(); i++) if(s[i]=='R') v.push_back(i+1);
    for(int i : v) if(i <= v.size()) cnt++;
    cout<<v.size()-cnt;
}

```

### **E - Logs**
N개의 log를 K회로 반씩 쪼개어 가장긴 log를 짧게 만드는 문제입니다.

>N = 2, K = 3, a1 = 7, a2 = 9
>
>log = {7,9} 일때는 7을 1회 반으로쪼갭니다.
>
>log = {3.5, 3.5, 9} 이후 9를 2회 쪼갭니다.
>
>log = {3.5, 3.5, 3, 3, 3} 가장긴 log의 길이는 3.5로 반올림하여 4가 답이됩니다.

가장 긴 log의 길이를 이분탐색하여 문제를 해결할 수 있습니다.

(ai-1)/mid 를 모두 더한값이 K를 초과하면 l = mid + 1 아니라면 r = mid - 1 로 이분탐색 합니다.

```c++
#include <bits/stdc++.h>

using namespace std;
int n,a[222222],k,l=1,r,ans;
bool check(int x){
    for(int i=1,ret=0; i<=n; i++){
        ret += (a[i]-1)/x;
        if(ret > k) return false;
    } return true;
}
int main(){
    ios_base::sync_with_stdio(0);cin.tie(nullptr);
    cin>>n>>k;
    for(int i=1; i<=n; i++){
        cin>>a[i];
        r = max(r,a[i]);
    }
    while(l <= r){
        int mid = l+r>>1;
        check(mid) ? r=mid-1,ans=mid: l = mid + 1;
    }
    cout<<ans<<'\n';
}
```

### **F - Range Set Query**

다양한 풀이가 있다고하나 저는 모스 알고리즘으로 해결하였습니다.

[수열과 쿼리 5](https://www.acmicpc.net/problem/13547) 이 문제와 같은문제입니다.

단순하게 모스로 쓱싹짜서 제출하였더니 야주조금 시간초과가 나서 GCC최적화 플래그를 박아 시간초과를 해결하였습니다.
{% raw %}
```c++
#include <bits/stdc++.h>
#pragma GCC optimize("O3")
#pragma GCC optimize("Ofast")
#pragma GCC optimization("unroll-loops")
#pragma GCC target("avx,avx2,fma")

#define prev ddd

using namespace std;
using pi = pair<int,int>;
using pii = pair<pi,int>;
vector<pi> v;
vector<pii> w;
int n,sqrtn,m,a[555555],check[555555],ans[555555],ret;
void add(int x){ret += ++check[x]==1;}
void del(int x){ret -= !--check[x];}
void go(int x){
    pi prev = {0,0},now = v[w[x].second];
    if(x) prev = v[w[x-1].second];
    for(int i=prev.first-1; i>=now.first; i--) add(a[i]);
    for(int i=prev.second+1; i<=now.second; i++) add(a[i]);
    for(int i=prev.first; i<now.first; i++) del(a[i]);
    for(int i=prev.second; i>now.second; i--) del(a[i]);
}
int main(){
    ios_base::sync_with_stdio(0);cin.tie(nullptr);
    cin>>n>>m;
    sqrtn = sqrt(n);
    for(int i=1; i<=n; i++) cin>>a[i];
    for(int i=0,x,y; i<m; i++){
        cin>>x>>y;
        v.push_back({x,y});
        w.push_back({{x/sqrtn,y},i});
    }
    sort(w.begin(),w.end());
    for(int i=0; i<m; i++){
        go(i);
        ans[w[i].second] = ret;
    }
    for(int i=0; i<m; i++) cout<<ans[i]<<'\n';
}

```
{% endraw %}