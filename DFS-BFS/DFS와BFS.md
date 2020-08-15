[문제](https://www.acmicpc.net/problem/1260)
--------------------------------------------

<br>

### 1. 코드

<br>

```cpp
#include <vector>
#include <iostream>
#include <string>
#include <queue>
#include <cstring>

using namespace std;

// 방문 여부를 저장하기 위한 배열인 visit의 크기
#define MAX 1001
int visit[MAX];
int map[MAX][MAX];
int N, M, V; // 정점 개수, 간선 개수, 시작 번호

void dfs(int v) {
	
	cout << v << ' ';

	visit[v] = 1;
	// 1 2 4 3 순서인데 3에 도달하면 
	for (int i = 1; i <= N; i++) {
		if (visit[i] == 1 || map[v][i] == 0) continue;
		visit[i] = 1;

		dfs(i);
	} 
}

void bfs(int v) {
	
	queue <int> q;
	q.push(v);
	visit[v] = 1;

	while (!q.empty()) {

		v = q.front(); // v = 5
		
		for (int i = 1; i <= N; i++) {	
	
			if (visit[i] == 1 || map[v][i] == 0) continue;
					
			visit[i] = 1;
			q.push(i);
		}
	
		q.pop();
		cout << v << ' ';
		
	} 
}

int main() {
	
	int x, y;

	cin >> N >> M >> V;

	for (int i = 0; i < M; i++) {
		cin >> x >> y;
		map[x][y] = 1;
		map[y][x] = 1;
	}

	dfs(V);
	cout << endl;

	memset(visit, 0, sizeof(visit));

	bfs(V);
	
	return 0;
}
```

<br>

### 2. 코멘트

    너무 많이 쓰이는 알고리즘이므로 꼭 기억하자
