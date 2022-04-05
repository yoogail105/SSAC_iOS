# 옵셔널 바인딩: if - let, guard



```swift
enum UserMissonStatus: String{
    case missionFailed = "실패"
    case missionSucceed = "성공"
}
```

### **1. 강제 해제 `!`**

```swift
func checkNumber(number: Int?) -> (UserMissonStatus, Int?) {
    //optional이 들어갈 공간이 없다. -> ? 적어준다.
    if number != nil {
        // nil이 아니라면: (절대 nil이 아니기 때문에) 강제 해제 연산자를 사용 가능
        return (.missionSucceed, number!)
    } else {
        return (.missionFailed, nil)
        //return (.missionFailed, 100000)
    }
}

```

### 옵셔널바인딩: if-let

```swift
//1. 조금 더 안전하게 하는 방법은?
func checkNumber2(number: Int?) -> (UserMissonStatus, Int?) {
    //number은 ?, value는 ?을 받아들일 수 없는 타입
    if let value = number {
        //value의 생명주기가 이곳 중괄호 안에서 끝난다.
        return (.missionSucceed, value)
    } else {
        return (.missionFailed, nil)
    }
    // 강제 해제 연산자 안쓰니까 -> 안정성을 높인 코드
}
```

### 3. 옵셔널바인딩: guard

```swift
func checkNumber3(number: Int?) -> (UserMissonStatus, Int?) {
    //guard: else부터 처리한다.
    guard let value = number else {
        return (.missionFailed, nil)
        //실패하면 누구보다 빠르게 반환을 해버린다.
    }
//value는 
    return (.missionSucceed, value)
}
```

![image](https://user-images.githubusercontent.com/53874628/161830279-4708363c-c097-434b-a85c-6833c44cac60.png)

![image](https://user-images.githubusercontent.com/53874628/161830324-d19c067c-24cb-44f7-be28-b91683399cf0.png)

- number는 원래 `Optional Int`이다.
- but. `if let value = number`가 참인 구문 안에서 value는 옵셔널이 아닌 `Int`이다.
    
    → 그래서 강제해제를 사용하지 않고도 value를 그대로 사용할 수 있다.
    
- if-let 과 guard-let의 차이
    - if-let: `value`가 중괄호 안에서만 처리 가능하다.
        
        (생명주기가 안에서 끝남)
        
    - guard-let: `value`가중괄호 밖에서도 사용 가능하다.
