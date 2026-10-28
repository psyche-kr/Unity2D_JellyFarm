# Jelly Farm

방치형 농장 시뮬레이션 게임입니다. Unity의 Bolt(Visual Scripting)로 만들었고, [GoldMetal](https://www.youtube.com/@goldmetal)의 Unity 강의를 참고해 따라 만들면서 로직을 직접 구성했습니다.

| 항목 | 내용 |
| --- | --- |
| 인원 | 1명 |
| 엔진 | Unity 2021.3.37f1 (Bolt / Visual Scripting) |
| 스크립트 | `Assets/JellyFarm/Scripts` (C# 2개), 나머지는 `Assets/JellyFarm/Graphs`의 비주얼 그래프 |

## 구현 내용

- **젤리 이동 AI**: 젤리가 걷고 멈추기를 반복하는 동작을 상태 머신(FSM)으로 짰습니다. (`Graphs/Jelly.asset`, `SuperUnit/SetWalk`, `CheckBorder`)
- **판매와 재화**: 젤리를 끌어다 판매하는 드래그 판매, 골드와 젤라틴 획득, 경험치 처리. (`ButtonSell`, `SuperUnit/GetGold`, `GetJelatin`, `SetExp`)
- **해금과 구매**: 패널에서 젤리와 식물을 구매하고 해금하는 시스템. (`JellyPanel`, `PlantPanel`, `ButtonPanel`, `SuperUnit/MakeJelly`)
- **저장과 불러오기**: 젤리 상태를 저장하고 다시 불러옵니다. (`SuperUnit/SaveJelly`)
- **옵션과 연출**: 옵션 설정, 알림 팝업, 효과음과 배경음 설정. (`ButtonOption`, `NoticeManager`, `SoundManager`, `SuperUnit/PlayNotice`, `PlaySound`)
- 반복해서 쓰는 노드 묶음은 `SuperUnit`으로 분리해 재사용했습니다.

## 배운 점

게임 동작 구조의 대부분을 IDE에서 코드를 쓰지 않고도 구현할 수 있다는 것을 확인했습니다. 상태 머신, 데이터 저장, UI 연출을 비주얼 노드로 구성해 보면서 내부 로직을 직접 설계하는 감각을 익혔습니다.
