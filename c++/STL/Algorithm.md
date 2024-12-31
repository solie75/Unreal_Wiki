# min_element

- 주어진 범위에서 가장 작은 값의 iterator를  반환한다.
- 범위가 비어있다면 last 를 반환한다.
- 최소값이 배열에 여러개 있을 때 가장 앞의 최소값의 iterator 를 반환한다.
```c++
template<class ForwardIt> 
ForwardIt min_element(ForwardIt first, ForwardIt last);

// 사용자 정의 비교 함수
template<class ForwardIt, class Compare>
ForwardIt min_element(ForwardIt first, ForwardIt last, Compare comp);
```