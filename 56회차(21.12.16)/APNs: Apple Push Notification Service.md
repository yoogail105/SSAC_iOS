# Apple Push Notification Service

- 서버에서 바로 기기로 보내지 않고, 반드시 APNs를 거쳐야 한다!
- APNs는 알림 전달을 시도
- 알림 대상 장치가 오프라인이면, 잠시 보류했다가 다시 온라인 될 때 전달한다.
- 기기 및 앱 별로 **가장 최근의 알림**만 저장을 한다.

  → 각 기기의 상태를 확인하여 전달한다.

### APNs의 보안

1. Connection trust 연결 신뢰
    
    서버 ↔ APNs: **승인된 공급자**만 APNs와 연결해서 푸시 알림을 전달
    
    승인된 공급자를 어떻게 확인할까?
    
    1. token-based: 유효한 인증키로 확인
    2. certificate-based: SSL 인증서 이용
    
    APNs ↔ 디바이스: **승인된 장치**만 APNs의 알림을 받을 수 있다!
    
    : APNs는 애플 생태계에 있는 장치와 connection trust를 자동으로 구성한다.
    
2. Device token trust
    
    : 각 원격 알림은 `**end-to-end**` 방식으로 작동한다.
    
    즉, 보내는 주체인 서버와, 받는 주체인  기기 사이에서만 전달된다.
    
    Device token은 애플이 특정 장치의 특정 앱에 할당한 고유 식별자를 포함하는 NSdata instance, 누군가가 토큰을 설치하더라도 내용을 해독할 수 없다!
