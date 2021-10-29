# #NWPathMonitor 구현하기

### 1. NWPathMonitor() 생성
: 파라미터를 주지 않으면 모든 네트워크 환경의 변화를 감지,

파라미터를 주면 특정하거나 제외할 수 있다.

<img width="457" alt="image" src="https://user-images.githubusercontent.com/53874628/139397883-ca432c3a-1bb3-4385-a6e9-12bbb7c61294.png">


```swift
let networkMonitor = NWPathMonitor()
let specificNetworkMonitor = NWPathMonitor(requiredInterfaceType: .wifi)
let prohibitNetworkMonitor = NWPathMonitor(prohibitedInterfaceTypes: [.wifi, .cellular])

```

### 2. NWInterface.InterfaceType의 종류
    
    :`.cellular` `.wifi` `.loopback` `.wiredEthernet` `.other
    
    <img width="452" alt="image" src="https://user-images.githubusercontent.com/53874628/139397853-32fbcb87-949b-4d30-99de-e8697a9217d4.png">
    

### 3. `networkMonitor.pathUpdateHandler`: `NWPath(상태)` 반환
    
    ```swift
    networkMonitor.pathUpdateHandler = { path in
    
    	if path.status == .satisfied {
    		print("Network Connected")
    	// NWInterface.InterfaceType의 종류 다양
    		if path.usesInterfaceType(.cellular) {
    		} else if path.path.usesInterfaceType(.wifi) {
    			} else {
    			}
    	} else {
    			print("Network Disconnected")
    	}
    	
    
    ```
    
### 4. 변화를 감지하기 위해서 시작메서드 호출하기
    
    ```swift
    	self.networkMonitor.start(queue: DispatchQueue.global())
    }
    ```
    
    ✔︎DispatchQueue.global()
    
    ∙GCD는 DispatchQuere라는 클래스에서, dispatch queues라는 큐를 관리한다.
    
    ∙GCD에 작업 전달 → GCD는 큐 선택 → 큐: 작업수행(IFIO
    
    ∙global 큐는 GCD에서 제공하는 큐 타입 중 하나이다.
    
    -동시에 여러 작업을 할 수 있는 Concurrent큐
    
    -우선순위에 따라, (high, default, low, background)로 4개가 존재.
    
    → global큐의 우선순위는 Qos로 결정.
    
    ∙ Qos는 우선순위가 높은 순서대로, User-interactive, User-initiated, Utility, Background가 있다.
    
### 5. 결과
    
   <img width="459" alt="image" src="https://user-images.githubusercontent.com/53874628/139397822-20f1f576-0904-4cbf-bd96-cdb8645ec01a.png">
    
    연결 상태가 변화될 때마다 상태 변화가 반환된다.
    
    (print문을 통해 출력하도록 작성했음)
    

🔖**참고**

∙ SSAC iOS 개발자 데뷔과정 강의와 강의자료</br>
∙[https://github.com/cleanios/Study/issues/1](https://github.com/cleanios/Study/issues/1)</br>
∙[https://rhammer.tistory.com/324](https://rhammer.tistory.com/324)</br>
