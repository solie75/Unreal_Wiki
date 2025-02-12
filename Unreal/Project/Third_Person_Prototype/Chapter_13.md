# 충돌 이벤트

Overlap 이벤트 : 물리적인 부딪힘 없이 엑터가 서로 겹치기 시작했을 때 발생
Hit 이벤트 : 실제 물리 충돌이 일어났을 때 발생.

- BaseItem
1. 아이템 발현 과정을 위한 컴포넌트 추가
	1. USceneComponent
	2. USphereComponent
		1. collision profile 성정.
		2. Overlap 이벤트 바인딩

```c++
// BaseItem.h
UPROPERTY(VisibleAnywhere, BlueprintReadWrite, Category = "Item|Component")
USceneComponent* Scene;

UPROPERTY(VisibleAnywhere, BlueprintReadWrite, Category = "Item|Component")
USphereComponent* Collider;

UPROPERTY(VisibleAnywhere, BlueprintReadWrite, Category = "Item|Component")
UStaticMeshComponent* StaticMesh;

// BaseItemcpp

// 생성자에서 충돌 관련 컴포넌트 초기화
ABaseItem::ABaseItem()
{
 	...

	// 컴포넌트 초기화
	Scene = CreateDefaultSubobject<USceneComponent>(TEXT("Scene"));
	SetRootComponent(Scene);

	Collider = CreateDefaultSubobject<USphereComponent>(TEXT("Collider"));
	// 충돌 프로파일 설정.
	Collider->SetCollisionProfileName(TEXT("OverlapAllDynamic"));
	Collider->SetupAttachment(Scene);
	
	StaticMesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("StaticMesh"));
	StaticMesh->SetupAttachment(Collider);

	// 충돌 이벤트 에 충돌 콜백 함수 바인딩.
	Collider->OnComponentBeginOverlap.AddDynamic(this, &ABaseItem::OnItemBeginOverlap);
	Collider->OnComponentEndOverlap.AddDynamic(this, &ABaseItem::OnItemEndOverlap);
}

// 충돌 콜백 함수
void ABaseItem::OnItemBeginOverlap(UPrimitiveComponent* OwnOverlappedComp, AActor* OtherActor, UPrimitiveComponent* OtherOverlappedComp, int32 OtherBodyIndex, bool bFromSweep, const FHitResult& SweepResult)
{
	if (OtherActor && OtherActor->ActorHasTag("Player"))
	{
		ActivateItem(OtherActor);
	}
}
void ABaseItem::OnItemEndOverlap(
	UPrimitiveComponent* OwnOverlappedComp,
	AActor* OverlapActor,
	UPrimitiveComponent* OtherOverlappedComp,
	int32 OtherBodyIndex)
{ }

void ABaseItem::ActivateItem(AActor* Activator)
{
	Destroy();
}
```

Overlap 이벤트에 바인딩 할 함수 수정.
ItemInterface 에 선언되어 있던 Overlap 이벤트 콜백 함수들을 수정한다.

```c++
// ItemInterface.h

UFUNCTION()
virtual void OnItemBeginOverlap(
	UPrimitiveComponent* OwnOverlappedComp,
	AActor* OverlapActor,
	UPrimitiveComponent* OtherOverlappedComp,
	int32 OtherBodyIndex,
	bool bFromSweep,
	const FHitResult& SweepResult
) = 0;

UFUNCTION()
virtual void OnItemEndOverlap(
	UPrimitiveComponent* OwnOverlappedComp,
	AActor* OverlapActor,
	UPrimitiveComponent* OtherOverlappedComp,
	int32 OtherBodyIndex
) = 0;
```

Iteml 의 ActivateItem

```c++
void ACoinItem::ActivateItem(AActor* Activator)
{
	if (Activator && Activator->ActorHasTag("Player"))
	{
		GEngine->AddOnScreenDebugMessage(
			-1,
			2.0f,
			FColor::Green,
			FString::Printf(TEXT("Player Gained %d points!"), PointValue)
		);
	}

	// Destroy
	Super::ActivateItem(Activator);
}
```

# 지뢰 아이템



# 아이템 획득

ui ai 애니메이션 서버 동기화


# Q.

Component 의 충돌과 Actor의 충돌. 둘을 각자 어느 상황에 다뤄야 할까.