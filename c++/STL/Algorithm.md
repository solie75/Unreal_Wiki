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

# lecixographical_compare

```c++
template< class InputIt1, class InputIt2, class Compare >  
bool lexicographical_compare( InputIt1 first1, InputIt1 last1,  
                              InputIt2 first2, InputIt2 last2,  
                              Compare comp );
```

- 첫 번째 범위  \[first1, last1] 가 사전식 정렬에 대해 두 번째 범위 \[first2, last2] 보다 작은지 확인한다.
- 첫 번째 범위가 두 번째 범위에 비해 사전식 정력에 대해 작다면 true 를 그렇지 않다면 false 를 반환한다.

# 함수 정리

CreateDefaultSubObject 

USceneComponent

SetRootComponent

SetUpAttachment

ConstructorHelpers

Succeeded

SetStaticMesh

SetMaterial
