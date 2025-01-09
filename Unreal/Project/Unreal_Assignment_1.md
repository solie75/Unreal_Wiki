Actor 를 생성하고, 생성된 Actor 를 랜덤하게 10번 이동.

- 필수
	1. (0,0) 에서 스폰 되며 spawn 될 때 로그 출력
	2. 게임 캐릭터가 랜덤하게 10 회 이동 -> 이때 변화된 좌표를 출력(UE_LOG 활용)
	3.  step 함수 :  한번에 이동할 x, y 값 반환
	4. move 함수 0,0 에서 10회 랜덤 이동 -> 좌표 출력; 이동 시 step 함수 활용.

- 순서
	1. Top Down 프로젝트 c++ 로 생성.
	2. 바닥 객체 에 Material 추가. (Tiling 으로 텍스쳐 비율 조절)
	3. Actor 생성. (Player)
	4. 플레이 시작 시 UI_LOG, AddOnScreenDebugMessage 로 좌표 출력.
	5. IA 와 IMC 생성 (space key 누르면 Move 함수 호출)
	6. 