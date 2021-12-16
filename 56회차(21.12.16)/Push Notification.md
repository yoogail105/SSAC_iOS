# Push Notification
- 서버에서 발생한 이벤트를 특정 사용자에게 전달하는 것
- Local Notification과 달리, 정해지지 않은 시간에 ```서버```에서 알림을 보낼 수 있는 방법
- 각종 어플들에서 휴대폰에 푸시 알림을 보내는 것, 그리고 카카오톡에서 메세지가 왔음을 알려주느 것 등이 있다.
- iOS에서는 Apple Push Notification System이라고 하는, APNS가 이를 담당한다.
- Firebase Cloud Messaging을 이용할 수 있다.

### 예시
1. 큐텐: 한 번에 **모든 사용자에게 같은 psuh내용**을 보낸다.
2. 날씨정보앱: **특정 위치에 있는 사람들에게 비가 온다는 정보**를 보낸다.
3. 카카오톡: 1대1 채팅처럼, **해당되는 디바이스에만 push**를 보낸다.

🔖 참고
- SSAC 강의 자료
- https://tech.junhabaek.net/백엔드-서버-아키텍처-presentation-layer-3-응답-유형에-따른-variation-2-push-notification-1eacb4df4a7e#1fcc
