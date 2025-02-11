class 가 엔진과 에디터의 다양한 부분과 어떻게 작동하는지를 지정하기 위해 UClass 선언시 사용되는 키워드.

# Blueprintable

해당 키워드가 선언된 클래스를 기반으로 블루 프린트 클래스 생성이 가능해진다. 
즉, Blueprintable 선언이 없는 클래스는 블루 프린트 클래스의 Base 클래스가 될 수 없다.

- 예시
new c++ class 에서 클래스 생성
```c++
// Test1.h
#pragma once

#include "CoreMinimal.h"
#include "UObject/NoExportTypes.h"
#include "Test1.generated.h"

/**
 * 
 */
UCLASS()
class UE_ASSIGNMENT1_API UTest1 : public UObject
{
	GENERATED_BODY()
	
};
```

![Without_Blueprintable.png](/Image/Unreal/Without_Blueprintable.png)

blueprintable 적용

```c++
// Test1.h
#pragma once

#include "CoreMinimal.h"
#include "UObject/NoExportTypes.h"
#include "Test1.generated.h"

/**
 * 
 */
UCLASS(Blueprintable)
class UE_ASSIGNMENT1_API UTest1 : public UObject
{
	GENERATED_BODY()
	
};
```

![[With_Blueprintable.png]]

# Sweep vs Collider