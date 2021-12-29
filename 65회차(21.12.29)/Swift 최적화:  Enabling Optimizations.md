## 1. Enabling Optimizaions

: 스위프트는 자체적으로 3가지의 최적화 수준을 제공하고 있다.

- -Onone

  **디폴트** 상태.

  개발 중에는 가급적 최적화를 고려하지 않고, 개발단계에서 확인할 수 있는 모든 디버그 정보를 보존한다.

  주로 Debug 모드에서 사용된다.

- -O

  대부분의 프로덕션 코드에 해당.

  출시 후에는 디버그 정보에 대해 어느정도 손실이 되더라도 적극적인 최적화를 수행한다.

- -Osize

  특수한 상태.

  컴파일러가 성능보다 코드의 크기를 우선시 한다.

- 최적화 설정하는 방법

  : Xcode프로젝트 - Targets - BuildSetting - `optimization`
  <img width="909" alt="image-20211229112251487" src="https://user-images.githubusercontent.com/53874628/147661183-9cdc2891-9655-4d30-bd96-7ed15a84fdc2.png">
<img width="751" alt="image-20211229112403256" src="https://user-images.githubusercontent.com/53874628/147661187-15892326-d9c1-40f7-9d83-80695bbf6796.png">
<img width="906" alt="image-20211229112510622" src="https://user-images.githubusercontent.com/53874628/147661193-c2821da3-d230-4f5a-8621-874c972ecf3a.png">
