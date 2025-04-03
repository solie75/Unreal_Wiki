# FString 서식지정자.

```c++
FString str = TEXT("asdf");
UE_LOG(LogTemp, Warning, TEXT("%s"), *str);
```
위와 같이 해주어야 한다.

# LNK2005 

"public: void __cdecl ISW_PlayerAnimLayerInterface::AttackLayer(void)" (?AttackLayer@ISW_PlayerAnimLayerInterface@@QEAAXXZ) already defined in SW_PlayerAnimLayerInterface.gen.cpp.obj

중복해서 선언된 문제

- case 1 : UFUNCTION(BlueprintImplementableEvent) 를 소스코드에서 구현한 경우. BlueprintImplementableEvent 로 선언된 함수는 블루프린트에서 구현되어야 하기 때문에 c++ 상의 소스코드의 구현부를 없앤다.

# MSB3073