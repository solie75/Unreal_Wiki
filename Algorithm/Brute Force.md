가능한 모든 경우의 수를 전부 시도해 보는 것.
자료의 크기가 작거나, 최적화된 알고리즘을 떠올리기 어려울 때, 검증을 위해 사용된다.

예를 들어 n개의 원소에 대해
	부분 집합을 전부 구하는 경우 2^n;
	순열 (모든 원소를 나열하는 경우)의 브루트 포스 : n!
	이중, 삼중 반복문 등을 이용한 모든 '조합' 탐색.\
등이 있다.

# 방법

1. 중첩 반복문

2. bitmasking

```c++
int main()
{
	vector<int> vec = {1, 2, 3};
	int size = vec.size();

	for (int i = 0; i < (1 << size); i++)
	{
		cout << "{ ";
		for (int j = 0; j < size; j++)
		{
			if (i & (1 << j))
			{
				cout << vec[j] << " ";
			}
		}
		cout << "}\n";
	}
}
```

1. [next_permutation](/c++/STL/Algorithm.md#next_permutation)

2. 백트래킹.


# 예시

