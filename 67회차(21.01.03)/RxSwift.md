# RxSwift

## Sequence: protocol

- 하는 역할: 반복문을 돌 수 있다.
  - 값을 반복할 수 있도록 타입에 접근해주기 때문에



## Iterator

- protocol
- Sequence와Iterator 두 가지의 protocol
- 이 프로토콜을 준수하고 있다면...



=> Observable



## Observable & Observer

✔︎ 이벤트 전달 Observable

​	ex. 계산기에서 버튼을 누름

​	ex. email, password를 입력함

✔︎ 전달받은 이벤트 처리 Observer

​	ex. 결과값을 화면에 보여줌(숫자)

​	ex. 알맞은 형식인지에 대해 경고문장(?) 처리



ex. 유튜브

Observable: 수많은 유튜브 채널들이 영상을 올림

	- 영상을 보내고
	- 이벤트를 전달하고
	- **계속** 이벤트를 전달하고

Observer: 내가 구독하고 있는 채널에 동영상이 올라왔을 때만 나에게 알림 옴

- 영상을 받아본다

- 이벤트를 처리한다

- **계속 관찰**하고 있어야 한다

  

  🙋 Observer가 없다면?

  ​	👉 아무일도 일어나지 않는다.

  🙋 나중에 Oberver가 생긴다면?

  ​	👉 Observer가 생긴 **그 이후부터** 처리가 일어난다.

  ​			✔︎ 이전에 생긴 데이터에 대해서는 처리가 일어나지 않는다.



- **Infinite observable sequences**: 횟수가 정해져있지 않고, 무한하다.

​		: UI에 관련된 것이 주로 이런 것

- **Finite observable sequences**: 횟수 정해져 있음

  ex. 크기가 큰 사진을 다운받을 때 -> 분할로 나누어져서 데이터 전달됨.

  ✔︎ 점진적 다운로드의 문제점

   1. 네트워크 연결 유실

   2. 다운로드 실패

   3. 상태 코드 오류

      👉 다운로드 완료

### Observable

이벤트를 전달하는 과정에 따른 **Life Cycle**

- **Emit**(이벤트를 방출한다) ☞ Next ☞ Append Buffer 처리 필요

  점진적 다운로드

  최신 데이터 전달

- Notification ☞ Completed ☞ ImageView Image 처리 필요

  다운로드 완료

- Notification ☞ Error ☞ Alert 처리 필요

  디코딩실패

  상태코드 오류

  네트워크 연결 유실

ex. 사진을 10번에 나누어서 전달할 때 2번까지 성공한 후 실패한다면, error 알림



***"Observer가 Observable을 구독하고 있다" 라고 말함.***


🔖 참고
SeSAC iOS 개발자 데뷔 과정 강의 자료
