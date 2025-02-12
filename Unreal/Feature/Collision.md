# Collision Presets

1. NoCollision
	1. 모든 collision 및 모든 overlap 비활성화
2. BlockAll
	1. 모든 collision 활성화, overlap 비활성화.
3. BlockAllDynamic
	1. 동적 오브젝트와의 충돌을 감지하지만, 정적 오브젝트는 제외
4. OverlapAll
	1. 모든 collision 비활성화, 모든 overlap 활성화
5. OverlapAllDynamic
	1. 모든 collision 비활성화, 동적 오브젝트와의 overlap 만 활성화
6. Pawn
	1. 플레이어가 벽을 통과할 수 없음
7. CharacterMesh
	1. 플레이어 캐릭터의 본체에 적용
	2. WorldStatic 에 대해 Block, Pawn 과는 Overlap
	3. 캐릭터의 머리나 팔 같은 특정 부위에만 Overlap 이벤트를 적용하고 싶을 때.
8. PhysicsActor
	1. 물리 시뮬레이션에 활성화


# Collision Enabled (충돌 활성화 옵션)

Collision Presets 를 Custom 으로 설정하면 Collision Enabled 를 직접 조정할 수 있다.


| 옵션               | physics (물리 시뮬레이션) | query (overlap) | query (physics) | 설명                                            |
| ---------------- | ------------------ | --------------- | --------------- | --------------------------------------------- |
| No Collision     | X                  | X               | X               | 충돌 및 오버랩 완전 비활성화 (장식, 연출용 이팩트 등)              |
| Query Only       | X                  | O               | X               | 충돌 및 오버랩 감지만 가능 (트리거 박스, 아이템 등)               |
| Physics Only     | O                  | X               | O               | 물리적 충돌만 감지, Overlap 및 Hit 이벤트 없음 (더비 물리 오브젝트) |
| Query and Physic | O                  | O               | O               | 충돌 감지와 물리 시뮬레이션 모두 가능. (플레이어, 차량, 총알)         |

# 코드에서 충돌 옵션 설정

- Collision Preset 설정
```c++
(충돌 컴포넌트)->SetCollisionProfileName(TEXT("OverlapAllDynamic"));
```

- Collision  Enabled 설정
```c++
(충돌 컴포넌트)->SetCollisionProfileName(TEXT("Custom"));
(충돌 컴포넌트)->SetCollisionEnabled(ECollisionEnabled::QueryAndPhysics);
// Object Type 설정.
(충돌 컴포넌트)->SetCollisionObjectType(ECC_WorldDynamic);
// 충돌 반응 설정.
(충돌 컴포넌트)->SetCollisionResponseToAllChannels(ECR_Ignore); // 기본적으로 모든 충돌 무시
(충돌 컴포넌트)->SetCollisionResponseToChannel(ECC_Pawn, ECROverlap); // 플레이어(Panw) 와는 overlap
(충돌 컴포넌트)->SetCollisionResponseToChannel(ECC_PhysicsBody, ECR_Block); // 물리 오브젝트와 충돌.
```

# Overlap vs Hit

