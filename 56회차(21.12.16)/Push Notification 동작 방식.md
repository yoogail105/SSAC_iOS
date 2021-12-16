# Push Notification 동작 방식

<img width="755" alt="image" src="https://user-images.githubusercontent.com/53874628/146339655-2bb93d45-1085-4f7f-a36a-d89693cd2a78.png">


- APNs(Apple Push Notification System)
- Push는 전세계적으로, 모두 APNs가 담당한다.
1. 앱을 켠 사용자(권한동의O)가 APNs에 토큰을 요청하게 된다.
2. APNs: 토큰에 대한 값을 사용자에게 전달한다. (특정 사용자의 앱에서만 인식될 수 있는 토큰)
3. 토큰을 서버에 전달
4. 서버 처리가 성공했는지, 실패했는지에 대한 정보를 준다.
5. 사용자가 자신이 가지고 있는 클라이언트값을 저장하게 되고, 이 값을 통해서 계속 통신하게 된다.
