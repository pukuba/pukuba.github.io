---
title: 백준 브루트 포스, 구현 문제풀이
layout: post
tags: BFS Brute-force simulation
categories: PS
date: 2021-01-30 21:06:00

--- 

브루트 포스, 구현 문제풀이


<details>
<summary>백준 9196 정수 직사각형</summary>
모든 w*w+h*h, h, w 를 벡터에 넣고 문제에 조건과 맞게 정렬한뒤 이분탐색으로 입력받은 값의 인덱스를 찾고 다음 인덱스의 값을 출력한다.
</details>

<details>
<summary>백준 18111 마인크래프트</summary>
블럭의 높이가 0~256 이기때문에 범위가 작다.

500 * 500 * 256 으로 각 모든 높이를 만들어보며 답을 구하면 된다.
</details>

<details>
<summary>백준 14891 톱니바퀴</summary>
<p>
deque을 이용하여서 쉽게 구현이 가능하다.

``` cpp
deque<int> d;
if(x == -1){
    d.push_back(d.front());
    d.front_pop();
}
else{
    d.push_front(d.back());
    d.pop_back();
}

```

x를 시계방향으로 회전한다면 x+1, x-1을 반시계 방향으로 회전하는것은 mod 연산을 통해서 쉽게 구할 수 있다.
</p>
</details>

<details>
<summary>백준 16988 Baaaaaaaaaduk2 (Easy)</summary>
점 2개를 모든 경우에 배치한 뒤 BFS를 돌려 돌을 잡을 수 있는지 확인하면 된다.

모든 칸에 2개의 점씩 배치해보는게 (NM)^2, BFS는 NM에 가능하다.
따라서 (NM)^3 에 해결이 가능하다.
</details>

<details>
<summary>백준 2615 오목</summary>
반복문을 돌면서 해당하는 좌표의 배열이 1 혹은 2라면 가로 세로 대각선으로 확인하면 된다.
</details>

<details>
<summary>백준 1239 차트</summary>
N의 범위가 8이기 때문에
배열을 정렬한 뒤 next_permutation()을 이용하여 모든 경우로 배열을 바꾸어보고, 그 후 연속된 원소의 합이 50이 나오는 경우의 수를 새면 된다.

* 원형이다 조심하자!

</details>

<details>
<summary>백준 17406 배열 돌리기 4</summary>
K의 범위가 6이하 이기 때문에
next_permutation() 을 이용하여 모든 순서를 다 만든뒤 연산을 하면 답을 구할 수 있다.

</details>