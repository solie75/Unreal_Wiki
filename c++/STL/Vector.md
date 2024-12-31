# capacity()

- 현재 벡터의 할당된 메모리 크기를 반환한다.
```c++
vector<int> arr{1,2,3};
cout << arr.capacity();
```

```c++
// 결과
3
```
# erase()

- 주어진 조건에 맞게 원소를 삭제한다.
- 정확히는 그 공간 자체를 삭제하는 것이 아니라 주어진 조건에 맞는 메모리 공간 의 값을 주어진 조건 뒷 부분의 값들로 '대체' 하는 것이다.
- erase 하는 만큼 size() 는 줄어들지만 할당된 공간 크기인 capacity()의 값은 변화가 없다.

- 정의
```c++
iterator erase (const_iterator position);
iterator erase (const_iterator first, const_iterator last);
```

- 예시
```c++
void print(vector<int>& _arr)
{
    cout << "=======================================" << "\n";
    cout << "element : ";
    for (int i = 0; i < _arr.size(); i++)
    {
        cout << _arr[i] << " ";
    }
    cout << "\n";
    cout << "capacity : " << _arr.capacity() << "\n";
    cout << "size : " << _arr.size() << "\n";
    cout << "address : ";
    vector<int>::iterator iter = _arr.begin();
    for (int i = 0; i < _arr.size(); iter++, i++)
    {
        cout << "\"" << &(*iter) << "\" ";
    }
    cout << "\n";
}

int main()
{
    vector<int> arr{ 10, 4, 6, 7, 3, 3, 9 };
    print(arr);
    arr.erase(arr.begin());
    print(arr);
    arr.erase(arr.begin(), arr.begin() + 3);
    print(arr);
}
```

```c++
// 결과
=======================================
element : 10 4 6 7 3 3 9
capacity : 7
size : 7
address : "0000026264A0F150" "0000026264A0F154" "0000026264A0F158" "0000026264A0F15C" "0000026264A0F160" "0000026264A0F164" "0000026264A0F168"
=======================================
element : 4 6 7 3 3 9
capacity : 7
size : 6
address : "0000026264A0F150" "0000026264A0F154" "0000026264A0F158" "0000026264A0F15C" "0000026264A0F160" "0000026264A0F164"
=======================================
element : 3 3 9
capacity : 7
size : 3
address : "0000026264A0F150" "0000026264A0F154" "0000026264A0F158"
```
- 주소를 보면 앞에서 부터 그대로인 것을 볼 수 있다. 이는 메모리 공간 자체를 삭제한것이 아니라 정해진 범위의 요소를 그 바로 뒤의 요소로 대체하고 주어진 범위만큼 size()를 줄인 것이라는 걸 알 수 있다.

