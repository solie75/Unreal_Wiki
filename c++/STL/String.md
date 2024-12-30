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