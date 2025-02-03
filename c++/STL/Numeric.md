# inner_product

```c++
_NODISCARD _CONSTEXPR20 _Ty inner_product(
    _InIt1 _First1, _InIt1 _Last1, _InIt2 _First2, _Ty _Val, _BinOp1 _Reduce_op, _BinOp2 _Transform_op);
_NODISCARD _CONSTEXPR20 _Ty inner_product(const _InIt1 _First1, const _InIt1 _Last1, const _InIt2 _First2, _Ty _Val);
```
- \_First1, \_Last1 : 첫 번째 범위의 시작과 끝을 나타내는 반복자.
- \_First2 : 두 번째 범위의 시작을 나타내는 반복자.

```c++
std::vector<int> vec1 = {1, 2, 3};
std::vector<int> vec2 = {4, 5, 6};
int dot = std::inner_product(vec1.begin(), vec1.end(), vec2.begin(), 0); 
// dot = 1*4 + 2*5 + 3*6 = 32
```
# accumulate

범위 내의 모든 요소를 누적하여 하나의 값을 계산한다.

```c++
std::vector<int> vec = {1, 2, 3, 4, 5};
int sum = std::accumulate(vec.begin(), vec.end(), 0); 
// sum 은 15
```

# adjacent_difference

범위 내에서 인접한 요소들 사이의 차이를 계산하여 다른 범위에 저장.
첫 번째 요소는 그대로 복사된다. 이후의 각 요소는 바로 이전 요소와의 차이가 계산된다.

```c++
vector<int> vec{ 1, 3, 6, 10 };
vector<int> diff(vec.size());
adjacent_difference(vec.begin(), vec.end(), diff.begin());
// diff 는 {1, 2, 3, 4} 이다.
```