[문제](https://www.acmicpc.net/problem/2875)
-----------------------

<br>
<br>

### 1. 코드 

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void solution(int n, int m, int k) {
	
	vector <int> answer = { 0 };

	for (int i = 0; i <= k; i++) {
		int temp_n = n;
		int temp_m = m;
		if (temp_n - (k - i) >= 0 && temp_m - i >= 0) {
			temp_n -= (k - i); temp_m -= i;
			answer.push_back(temp_n / 2 <= temp_m ? temp_n / 2 : temp_m);
		}
	}

	cout << *max_element(answer.begin(), answer.end());
}

int main() {
	int a, b, c;

	cin >> a >> b >> c;

	solution(a, b, c);
}
```

<br>

### 2. 코멘트

    핵심 알고리즘도 좋지만 반례가 없는지 살펴야 한다. 
