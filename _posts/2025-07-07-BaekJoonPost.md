---
title: "[공부] 백준 10989 수 정렬하기 3 C++"
date: 2025-07-07 17:00:00 +0900
categories:
  - 공부
  - 백준
tags:
  - 개발
  - 백준
  - 공부
pin: false
---

# 📝 문제

- 백준 10989 수 정렬하기 3
	- [https://www.acmicpc.net/problem/10989](https://www.acmicpc.net/problem/10989)

---

## 🔍 문제 상황
![문제 상황](assets/img/Baekjoon/Pasted image 20250707162733.png)
![문제 상황2](assets/img/Baekjoon/Pasted image 20250707162818.png)

---

## 💡 해결 방법 / 접근 방식

- 처음에는 단순히 수 정렬로 생각하고, n의 범위가 10,000,000(천만개)이기에 vector와 sort를 사용하여 풀어보고자 하였습니다.
- 하지만 문제의 시간 제한 및 메모리 제한을 파악하지 않은채 풀었고, 그결과 "메모리 초과"가 엄청 생겼습니다...
### 재접근
- 다시금 문제를 보았고, 메모리 제한이 있음을 파악하였습니다.
```cpp
vector<int> v;
v.resize(n);
```
- 을 할 시에 4bytes x 10,000,000 = 약 40MB의 메모리를 사용해서, 메모리 제한인 8MB를 넘는 현상이 발생합니다.
- 그래서 이를 해결하려면 "Counting Sort(계수 정렬)"을 써야 합니다.
### Counting Sort(계수 정렬)
1. 입력 받은 수를 인덱스에 개수로 저장
2. 정렬 필요 x - 그냥 인덱스 순서대로 출력하면 자동 정렬된 상태
3. 각 숫자가 몇 번 등장 했는지에 따라 출력
### 진행
- 문제 내에서 N은 10000보다 작거나 같은 자연수라고 하였기 때문에
- 정수형 배열로 하면
	- 4B x 10001 = 약 40KB이므로 메모리 제한(8MB)내 여유가 있습니다.
	```cpp
		int arr[10001] = {};
	```
---

## 🛠️ 구현 코드
```cpp
#include <iostream>  
#include <algorithm>  
  
using namespace std;  
  
int n;  
  
int main() {  
    ios_base::sync_with_stdio(false);  
    cin.tie(NULL);  
    cout.tie(NULL);  
  
    cin >> n;  
    int arr[10001] = {};  
    for (int i = 0; i < n; ++i) {  
        int in;  
        cin >> in;  
        arr[in] += 1;  
    }  
    for (int i = 0; i < 10001; ++i) {  
        for (int j = 0; j < arr[i]; ++j) {  
            cout << i << "\n";  
        }  
    }  
    return 0;  
}
```

## 🧷 결론
- 문제를 풀때 반드시 메모리 제한 등도 확인해봐야겠다는 생각이 들었고, "계수 정렬"이라는 방식도 알아볼 수 있었습니다.
- 또한 메모리 계산도 비슷한 문제들을 풀어보면서 메모리 초과가 안나게 풀어보는 연습을 해봐야할 것 같습니다 ㅎㅎ