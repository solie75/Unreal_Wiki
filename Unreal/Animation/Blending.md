https://dev.epicgames.com/documentation/en-us/unreal-engine/animation-blueprint-blend-nodes-in-unreal-engine#deadblendnodereference

- 크로스 페이드 (전통적 블렌딩) : 두 포즈를 동시에 평가해 알파 보간.
	- 작동방식 : 전환 구간 동안 **출발 포즈**와 **도착 포즈**를 동시에 매 프레임 평가해,  알파( α ) 값을 0→1로 증가시키며 `BlendedPose = Lerp(Source, Target, α)` 형태로 선형 보간.
	- 장점 : 구현이 단순하고 모든 애니메이션에 적용 가능
	- 한계 : 두 포즈의 차이가 크면 **팝핑(popping)**·**미끄러짐(foot sliding)** 발생 전환 시간 동안 **두 포즈를 모두 계산**하므로 CPU 비용 증가
- 관성 블렌딩 (Inertial Blending) : 출발 포즈를 더 이상 계산하지 않고 ' 관성' 정보로만 감쇠/ 예측해 전환
	- 작동 방식 : 전환이 시작되는 한 프레임에 **출발 포즈**의 뼈 위치·속도를 기록 → 이후 출발 포즈는 **계산 자체를 중단**
		- **Inertialization 노드** : “출발 ↔ 도착” 오프셋을 시간에 따라 감쇠해 0으로 수렴
		- **Dead Blending 노드** : 출발 포즈를 _미래 방향으로 예측_해 크로스페이드
	- 장점
		- 출발 포즈를 더 이상 평가하지 않아 **성능↑**
		- 포즈 차이가 커도 관성(속도·궤적)을 이용해 **자연스러운 이어짐**
		- 짧은 블렌드에서도 부드러움 유지

- natural transitions as a post-process 이란? : 그래프 평가 후 단일 노드에서 관성 보간을 수행해, 짧은 시간에도 튀지 않는 부드러운 애니메이션 전환구현.
	- Post-Process : 일반적인 애님 그래프 평가가 끝난 **마지막 단계**에서 ‘덧입히는’ 방식. 이미 계산된 도착 포즈만 가지고 보간·예측을 수행하므로 그래프 구조를 크게 바꾸지 않아도 됨.
	- 뼈의 **위치·속도(관성)**, 커브 값을 활용해 실제 물체가 관성으로 움직이듯 부드럽게 감쇠
	- 발이 땅에 붙어 있어야 하는 캐릭터 등에서 슬라이딩, 튐 현상 최소화
	- 짧고 빈번한 전환 (콤보 공격, 3인칭 슈팅 리코일 등)에서도 **팝 없이** 매끈한 연결을 제공하며, CPU·메모리 사용량은 전통적 크로스페이드보다 적다.