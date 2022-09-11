# Remote Notification 동작 방식

<img width="429" alt="image" src="https://user-images.githubusercontent.com/53874628/146376148-a81bfeac-a22c-4051-9a5f-334ed5eda5c6.png">
<img width="450" alt="image" src="https://user-images.githubusercontent.com/53874628/146377200-059bf3a5-7f70-4b83-a79e-8134c8f96eb0.png">

1. 📱 -> ☁️🔒</br>디바이스(Client App)는 APNs에 등록을 요청한다.(= `Device token`을 요청한다.)</br></br>
2. ☁️🔒 -> (🔑) -> 📱</br>APNs는 디바이스(Client App)에 `Device token`을 반환해 준다.</br></br>
3. 📱-> (🔑) -> ⚙️</br> 디바이스(Client App)은 Provider(서버, ex.Firebase)에 전달받은 `Device token`을 전달한다.</br></br>
4. ☁️🔒 -> (📝🔑) -> ☁️🔒</br>서버는 전달할 push내용과 `Device token`을 APNs에 전달한다.</br></br>
5. ☁️🔒 -> (📝) -> 📱</br>APNs는 `Device token`을 매치해 보고, 허용된 사용자라면 기기에 **`push notification`** 을 보낸다.
