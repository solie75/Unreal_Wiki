# GetConsoleCursorInfo

```c++
BOOL GetConsoleCursorInfo( 
	HANDLE hConsoleOutput, 
	PCONSOLE_CURSOR_INFO lpConsoleCursorInfo 
);
```
- hConsoleOutput : 콘솔 출력 핸들
- lpConsoleCursorInfo : 커서 정보를 저장할 `CONSOLE_CURSOR_INFO` 구조체의 포인터
- 성공 시 `TRUE`, 실패 시 `FALSE`를 반환하며, `GetLastError`로 오류 정보를 확인

# SetConsoleCursorInfo

```c++
BOOL SetConsoleCursorInfo( 
	HANDLE hConsoleOutput, 
	const CONSOLE_CURSOR_INFO* lpConsoleCursorInfo 
);
```
- hConsoleOutput : 콘솔 출력 핸들
- lpConsoleCursorInfo : 변경할 커서 정보를 포함한 `CONSOLE_CURSOR_INFO` 구조체의 포인터
- 성공 시 **`TRUE`**, 실패 시 **`FALSE`**를 반환하며, `GetLastError`로 오류 정보를 확인

# GetStdHandle

```c++
HANDLE GetStdHandle(DWORD nStdHandle);
```
# SetConsoleScreenBufferSize

```c++
```

# SetConsoleWindowInfo

```c++
```