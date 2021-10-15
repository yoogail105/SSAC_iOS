# # Tuple

## 1. Tuple?

0. Objective-C 에는 없었던, Swift에서 소개된 새로운 타입.

1. `**(val1, val2, val3)**`
2. `그룹 안의 값**member**들은 다양한 타입이 들어갈 수 있고, **tuple** 역시 멤버가 될 수 있다.`
    
    :named type, compound type, function type
    
3. `각 멤버들에 접근하려면` **`.Index`** `를 이용한다.`
4. `각 멤버들에 대해서도 이름을 줄 수 있다.`
    
    → `**.element's name`** 으로 접근할 수 있다.
    
    ```swift
    let someTuple = (22, true, "스트링")
    someTuple.0   //22
    someTuple.1   //true
    someTuple.2   //"스트링"
    
    let otherTuple = (22, (true, "스트링"))
    otherTuple.1   //(.0 true, .1 "스트링")
    otherTuple.1.1   //"스트링"
    
    func calculateAdd() {}
    func changedMenu() {}
    let functionInTuple = (calculateAdd(), changedMenu())
    
    var userData = (height: 170, weight: 65)
    userData.height   //170
    userData.weight   //65
    
    userData.height = 180
    userData.weight = 60
    userData   //(height 180, weight 60)
    ```
    

1. `Tuple은 함수의 return값이 될 수 있다.`
    
    (일반적으로 이렇게, 함수로 부터 다양한 값을 반환할 때 사용된다)
    
    ```swift
    func userProfile() -> (name: String, hegiht: Int, weight: Int) {
    	return ("yooga", 170, 65)
    }
    
    userProfile()   //(name "yooga", hegiht 170, weight 65)
    ```
    

## 2. Tuple 주의 사항

1. tuple에 아이템을 추가하거나 지울 수  없다.
2. 한 번 선언된 tuple 멤버의 `**타입**`을 바꿀 수 없다.
    
    ```swift
    var userData = (height: 170, weight: 65)
    userData = (155, 50)
    userData = ("yooga", 50) // 안된다!
    ```
    

## 3. Tuple과 typealias
- 🔖[출처](https://zeddios.tistory.com/238)

- `typealias`: 타입에 부를 대체어를 만들어 주는 것.

```swift
typealias UserProfile = (name: String, (height: Int, weight: Int))
var userProfile: UserProfile = ("Joe", (170, 60))

typealias UserProfile = (name: String, (height: Int, weight: Int))
var userProfile: UserProfile = ("Aiki", (170, 65))

// tuple들을 가진 배열 만들어 주기
var userProfiles: [UserProfile] = [("Joe", (170, 60)), ("Maz", (160, 50))]

// 값에 접근하기
userProfiles[0]   // (name "Joe", (height 170, weight 60))
userProfiles[0].0   // "Joe"
```

## 4. Tuple을 이용한 함수 예시
- 🔖[출처](https://www.hackingwithswift.com/search/tuple)

```swift
func split(name: String) -> (firstName: String, lastName: String) {
    let split = name.components(separatedBy: " ")
    return (split[0], split[1])
}

let parts = split(name: "Jorja Smith")

parts.0
parts.1
parts.firstName
parts.lastName

print("성: \(parts.lastName), 이름: \(parts.firstName)")
// 성: Smith, 이름: Jorja
```

</br>
</br>

🔖 참고
* [https://docs.swift.org/swift-book/ReferenceManual/Types.html#grammar_tuple-type-element](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html)
* [https://zeddios.tistory.com/238](https://zeddios.tistory.com/238)
* [https://www.hackingwithswift.com/search/tuple](https://www.hackingwithswift.com/search/tuple)
