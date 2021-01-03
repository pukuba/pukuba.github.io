---
title: 앳코더 Flat Subsequence 풀이
layout: post
tags: Segment-Tree AtCoder
categories: PS
date: 2021-01-04 05:06:00

--- 

앳코더 ACL 비기너 콘테스트 D번 (ACL Beginner Contest D)

###  **문제** 
* https://atcoder.jp/contests/abl/tasks/abl_d


###  **알고리즘** 
* 세그먼트 트리


###  **풀이**
원소의 차이가 K 이하인 LIS를 구하는 문제.

세그먼트 트리로 LIS를 O(NlgN) 에 구할수 있습니다.

세그먼트 트리를 이용하여 구간에서의 max를 O(lgN)에 구할수 있습니다.

A = (1, 3, 10, 5, 4, 8, 9)

K = 3

답 = 5 (1, 3, 5, 8, 9) 

Ai 는 언제나 30만 이하이기 때문에 세그먼트 트리를 이용할 수 있습니다.

세그먼트 트리로 현재 원소보다 k작은수, k큰수를 범위로 하고 범위에서의 가장 큰 수를 O(lgN)에 구합니다.

그후 O(lgN)의 시간복잡도로 현재 원소의 값에 위치하는 세그먼트 트리의 인덱스를 범위내 가장 큰 수 +1 로 업데이트 합니다.

### **조심해야 하는점**

1: 세그먼트 트리에서 쿼리를 날릴때 범위를 조심해야 합니다. (음수)

``` cpp
int MXN = 300000;
int l = max(1,a[i]-k), r = min(MXN,a[i]+k);
```

2: 세그먼트 트리의 인덱스는 1부터 시작합니다. Ai는 0부터 시작합니다. Ai의 값을 1씩 올려주기.

### 정답 코드

``` cpp
#include <bits/stdc++.h>

using namespace std;
int n,k,tree[2222222],MXN=300005;
int update(int node,int s,int e,int pos,int v){
    if(pos > e || s > pos) return tree[node];
    if(s == e) return tree[node] = v;
    return tree[node] = max(update(node*2,s,s+e>>1,pos,v),update(node*2+1,(s+e>>1)+1,e,pos,v));
}
int query(int node,int s,int e,int l,int r){
    if(s > r || e < l) return 0;
    if(l <= s && e <= r) return tree[node];
    return max(query(node*2,s,s+e>>1,l,r),query(node*2+1,(s+e>>1)+1,e,l,r));
}
int main(){
    ios::sync_with_stdio(0);cin.tie(0);
    cin>>n>>k;
    for(int i=1,x; i<=n; i++){
        cin>>x;
        ++x;
        int l = max(1,x-k),r = min(MXN,x+k);
        int q = query(1,1,MXN,l,r);
        update(1,1,MXN,x,q+1);
    }
    cout<<query(1,1,MXN,1,MXN);
}
```

