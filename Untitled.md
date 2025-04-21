```c++
// Fill out your copyright notice in the Description page of Project Settings.


#include "SW_PlayerState.h"
#include "AbilitySystem/SW_AbilitySystemComponent.h"
#include "AbilitySystem/SW_AttributeSet.h"

ASW_PlayerState::ASW_PlayerState()
{
	SetNetUpdateFrequency(100.f);

	AbilitySystemComponent = CreateDefaultSubobject<USW_AbilitySystemComponent>("AbilitySystemComponent");
	AbilitySystemComponent->SetIsReplicated(true);
	AbilitySystemComponent->SetReplicationMode(EGameplayEffectReplicationMode::Mixed);

	AttributeSet = CreateDefaultSubobject<USW_AttributeSet>("AttributeSet");
}

UAbilitySystemComponent* ASW_PlayerState::GetAbilitySystemComponent() const
{
	return AbilitySystemComponent;
}

USW_AttributeSet* ASW_PlayerState::GetAttributeSet() const
{
	return AttributeSet;
}

```

```c++
// Fill out your copyright notice in the Description page of Project Settings.

#pragma once

#include "CoreMinimal.h"
#include "GameFramework/PlayerState.h"
#include "AbilitySystemInterface.h"
#include "SW_PlayerState.generated.h"

class USW_AbilitySystemComponent;
class USW_AttributeSet;

UCLASS()
class TEAM4_CH4_PROJECT_API ASW_PlayerState : public APlayerState, public IAbilitySystemInterface
{
	GENERATED_BODY()
public:
	ASW_PlayerState();

protected:
	UPROPERTY()
	TObjectPtr<USW_AbilitySystemComponent> AbilitySystemComponent;

	UPROPERTY()
	TObjectPtr<USW_AttributeSet> AttributeSet;

public:
	virtual UAbilitySystemComponent* GetAbilitySystemComponent() const override;
	USW_AttributeSet* GetAttributeSet() const;
};

```