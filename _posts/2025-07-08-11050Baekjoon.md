---
title: "[공부] 백준 11050 이항 계수 1 C++"
date: 2025-07-08 20:10:00 +0900
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

- 백준 11050 이항 계수 1
	- [https://www.acmicpc.net/problem/11050](https://www.acmicpc.net/problem/11050)

---

## 🔍 문제 상황
![문제 상황](assets/img/Baekjoon/Pasted image 20250708200127.png)

---

## 💡 해결 방법 / 접근 방식

- 우선, 문제는 2개의 입력을 받고, 2개의 입력에 대한 이항 계수를 구하는 문제입니다.

### 이항 계수(Binomial Coefficient)란?
- 주어진 크기 집합에서 원하는 개수만큼 순서 없이 뽑는 조합의 가짓수를 일컫습니다.
![공식](assets/img/Baekjoon/Pasted image 20250708200435.png)
- 위와 같이 공식을 가지고 있으며, 복잡해보이지만 단순하게 보면 **n! / (n-k)!k!** 공식을 확인할 수 있습니다.
- 출처: [https://shoark7.github.io/programming/algorithm/3-ways-to-get-binomial-coefficients](https://shoark7.github.io/programming/algorithm/3-ways-to-get-binomial-coefficients)
### 접근 방식
- 위에서 파악한 공식이 **이항 계수 = n! / (n-k)!k!** 이기에,
- 우선 각 팩토리얼을 구한 후 나누기 및 곱하기를 진행해도 괜찮을 것 같다는 생각이 들었습니다.
- 구현이 쉬운 반복문을 통해 우선 팩토리얼을 구현하고, 각각에 맞는 n, n-k, k를 집어 넣어서 팩토리얼 값을 구하게 하였습니다.
- 그 후에, 나누기 및 곱하기를 진행하여 최종 결과를 출력하였습니다.
- 아래는 해당 코드입니다.

---

## 🛠️ 구현 코드
```cpp
#include <iostream>

using namespace std;

int n, k, result4;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    cin >> n >> k;
    // 이항 계수 = n! / (n-k)!k!
    int result1 = 1;
    for (int i = n; i > 0; --i) {
        result1 *= i;
    }
    int result2 = 1;
    for (int i = n - k; i > 0; --i) {
        result2 *= i;
    }
    int result3 = 1;
    for (int i = k; i > 0; --i) {
        result3 *= i;
    }
    result4 = result1 / (result2 * result3);
    cout << result4 << "\n";
    return 0;
}

```

## 🧷 결론
- 이번 문제는 이항 계수의 공식 및 팩토리얼 구현만 할줄 안다면 쉽게 구현 가능합니다.
- 다만, 실수로 result 변수를 int result = 0; 식으로 초기화를 해버리면 팩토리얼 구조상 값들이 곱해져야 하는데, 0에 곱해지는 탓에 결과가 0으로 나올 수 있으니 주의가 필요합니다.
- 또한, 팩토리얼을 반복문만으로가 아닌 팩토리얼 함수 등을 통해서 구하게 된다면 더 코드가 줄어들 수 있을 것 같습니다.