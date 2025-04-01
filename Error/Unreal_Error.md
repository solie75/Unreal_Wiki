# FString 서식지정자.

```c++
FString str = TEXT("asdf");
UE_LOG(LogTemp, Warning, TEXT("%s"), *str);
```
위와 같이 해주어야 한다.