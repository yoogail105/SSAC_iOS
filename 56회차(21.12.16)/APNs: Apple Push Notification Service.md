# Apple Push Notification Service

- 서버에서 알림을 바로 기기로 보내지 않고, 반드시 APNs를 거쳐야 한다!
- APNs는 알림 전달을 시도
- 알림 대상 장치가 오프라인이면, APNs는 제한된 시간동안 알림을 저장했다가 장치가 다시 온라인이 될 때 전달한다.
- 기기 및 앱 별로 **가장 최근의 알림만** 저장을 한다.<br>
  → 각 기기의 상태를 확인하여 전달한다.
    - 오프라인 상태에서 알림이 여러개 전달되면 각 서버의 가장 최신 알림만 저장, 기존 것은 삭제
    - 장치가 너무 오랜 시간동안 오프라인이면 저장된 알림을 모두 삭제

### APNs의 보안

1. Connection trust 연결 신뢰<br>
    1. 서버 ↔ APNs: **승인된 공급자**만 APNs와 연결해서 푸시 알림을 전달<br>
    🙋 승인된 공급자를 어떻게 확인할까?
      - token-based: 유효한 인증키로 확인
      - certificate-based: SSL 인증서 이용<br><br>
    2. APNs ↔ 디바이스: **승인된 장치**만 APNs의 알림을 받을 수 있다!<br>
    - APNs는 애플 생태계에 있는 장치와 connection trust를 자동으로 구성한다.
    
2. Device token trust
    - 각 원격 알림은 **`end-to-end`** 방식으로 작동한다.<br>
    - 즉, 보내는 주체인 올바른 서버와, 받는 주체인 올바른 기기 사이에서만 전달된다.
    - Device token은 애플이 특정 장치의 특정 앱에 할당한 고유 식별자를 포함하는 NSdata instance로, 누군가가 토큰을 탈취하더라도 안에 있는 내용을 해독할 수 없다! (APNs만 해독할 수 있음)

🔗 [APNs를 통한 Remote Notification 동작 방식](https://github.com/yoogail105/SSAC_iOS/blob/0d789872aa7cb0671eb465ba2940af0dac91f2eb/56%ED%9A%8C%EC%B0%A8(21.12.16)/Remote%20Notification%20%EB%8F%99%EC%9E%91%20%EB%B0%A9%EC%8B%9D.md)
