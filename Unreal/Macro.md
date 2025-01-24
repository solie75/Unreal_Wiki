# UE_LOG

- form
```c++
/**
 * A macro that logs a formatted message if the log category is active at the requested verbosity level.
 *
 * @param CategoryName   Name of the log category as provided to DEFINE_LOG_CATEGORY.
 * @param Verbosity      Verbosity level of this message. See ELogVerbosity.
 * @param Format         Format string literal in the style of printf.
 */
#define UE_LOG(CategoryName, Verbosity, Format, ...) \
```

- Custom LogTemp Category
```c++
// header file
DECLARE_LOG_CATEGORY_EXTERN(로그카테고리 이름, Waring, All);
```

```c++
DEFINE_LOG_CATEGORY(로그카테고리 이름);

...

UE_LOG(로그카테고리 이름, Warning, TEXT("로그에 출력할 내용"))
```

- Log Verbosity
	- Fetal
		- 빨간색 배경 + 흰색 텍스트
		- 프로그램 실행 주 치명적 오류로 인한 강제 종료가 필요할 시
	- Error
		- 빨간색 텍스트
		- 해결이 필요한 심각한 오류
	- Warning
		- 노락색 텍스트
		- 주의가 필요한 상황
	- Display
		- 흰색 텍스트
		- 기본 출력
	- Log
		- 회색 텍스트
		- 디버깅 관련된 일반 로그
	- Verbose
		- 짙은 회색 텍스트
		- 자세한 디버깅 정보 출력
	- VeryVerbose
		- 짙은 회색 텍스트
		- 최대한의 디버깅 정보 출력. 일반저그올 개발 중 특정 문제를 깊이 분석할 때 사용.