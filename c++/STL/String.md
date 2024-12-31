# define

```c++
using string = std::basic_string<char, std::char_traits<char>, std::allocator<char>>;
```
- string 은 char 을 저장한다 -> string 은 char 배열이다.
# operator \[ ]

```c++
int main()
{
	string str = "abcdefg";
	str[3] = '?';

	cout << str;
	return 0;
}
```

```c++
// 결과
abc?efg
```

# pop_back

```c++
int main()
{
	string str = "abcdefg";
	cout << str << "\n";
	str.pop_back();
	cout << str << "\n";
	return 0;
}
```

```c++
// 결과
abcdefg
abcdef
```

# push_back

```c++
int main()
{
	string str = "abcdefg";
	cout << str << "\n";
	str.push_back('?');
	cout << str << "\n";
	str.push_back('zzz');
	cout << str << "\n";
	return 0;
}
```

```c++
// 결과
abcdefg
abcdefg?
abcdefg?z
```

- push_back 은 한 번에 한 문자만 추가할 수 있다. (문자열 추가는 append)

# append

```c++
int main()
{
	string str = "abcdefg";
	cout << str << "\n";
	str.append(" namd : Jack");
	cout << str << "\n";
	return 0;
}
```

```c++
abcdefg
abcdefg namd : Jack
```

# replace

```c++
int main()
{
	string str = "abcdefghijk";
	cout << str << "\n";
	str.replace(3, 5, "zzz");
	cout << str << "\n";
	str.replace(str.begin() + 3, str.end() - 2, "???");
	cout << str << "\n";
	return 0;
}
```

```c++
// 결과
abcdefghijk
abczzzijk
abc???jk
```

- replace(int \_start, int \_length, string \_input)
	- \_start 인덱스 부터 \_length 만큼 을 \_input 으로 변경한다.
- replace(iterator \_start, iterator \_end, string \_input)
	- \_start 부터 \_end 까지 \_input 으로 변경한다.

# substr

문자열의 일부를 리턴한다.
```c++
basic_string substr(size_type pos = 0, size_type count = npos) const;
```
pos 부터 count 길이 만큼의 문자열을 리턴한다. count 의 길이가 문자열보다 길다면 그 이상을 반환하지 않고 문자열의 끝까지만 리턴한다.
count 로 npos 를 전달한다면, 자동으로 pos부터 원리 문자열의 끝까지 리턴한다.
pos 가 string 의 범위 밖이라면 오류를 발생시킨다.

- 예시
```c++
int main()
{
    string str = "0123456789abcdefghij";

    string sub1 = str.substr(10);
    cout << sub1 << "\n";

    string sub2 = str.substr(5, 3);
    cout << sub2 << "\n";

    string sub3 = str.substr(str.size() - 3, 50);
    cout << sub3 << "\n";
}
```

```c++
// 결과
abcdefghij
567
hij
```