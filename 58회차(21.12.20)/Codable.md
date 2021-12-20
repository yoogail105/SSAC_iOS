# Codable

## Codable

`codable`? 

```markdown
<span style="color:#3E8E7E">Red Text</span>
```

**JSON데이터를 <span style="color:#3E8E7E">간편하고, 쉽게 Encoding / Decoding</span>  할 수 있게 해 주는 프로토콜.**

- **<span style="color:#3E8E7E">`Encoding`</span> ?**

​	: struct, class, enum 등의 인스턴스를 **JSON형태의 데이터로!**

- **<span style="color:#3E8E7E">`Decoding`</span> ?**

​	: JSON형태의 데이터를 struct, class, enum 등의 **인스턴스로!**



Xcode에서 Codable 정의를 살펴보면, 

**Codable**은 **Encodable, Decodable 프로토콜**의 *typealias*이다.

![image-20211220152919834](/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220152919834.png)

- Codable은 struct, class, enum 등 모두가 채택할 수 있으며, 보통 struct를 선호한다.



## Decoding



## Encoding

✔︎ Encoding은 앞서 말했듯이, 인스턴스를 JSON형식의 데이터로 변환하는 것이다.

```swift
struct Student: Codable {
  var name: String
  var grade: Int
  var major: String
}

let Sol: Student = .init(name: "Sol", grade: 3, major: "Psychology")
```

Codable을 이용해 Sol이라는 구조체 변수를 Encoding하는 방법은,

```swift
let encoder = JSONEncoder()
let jsonData = try? encoder.encode(sol)
```

로 간단하다. 그런데 위와 같이만 코드를 작성하면 `45 bytes` 라는 값이 나오기 때문에, 이를 String으로 변환해야 한다.



do-try구문을 통해 변환을 하면

```swift
do {
    let jsonData = try encoder.encode(sol)
    guard let jsonString = String(data: jsonData, encoding: .utf8) else { fatalError("Failed") }
    print(jsonString)
} catch {
    print(error)
}
```

<img src="/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220165029634.png" alt="image-20211220165029634" style="zoom:50%;" />

요런 결과가 나온다.

지금은 변수가 **하나**이니까 그나마 쉽게 알아볼 수 있지만,, *<span style="color:#BDD2B6">(사실 나는 지금도 보기 어려움)</span>*

만약에 인코딩을 할 자료들이 아주 많아지는 경우라면, 다음과 같이 **<span style="color:#406882">*가독성*</span>**이 현저하게 떨어질 것이다.

![image-20211220164920972](/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220164920972.png)



### * .prettyPrinted

👉 보기 좋게 하는 방법은,

```swift
let encoder = JSONEncoder()
encoder.outputFormatting = .prettyPrinted
```

위의 코드를 사용하면 이름처럼,, ***pretty***하게.. 바꾸어준다.

<img src="/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220164846777.png" alt="image-20211220164846777" style="zoom:50%;" />



### * encode()

​    let jsonData = try encoder.**<span style="color:#6998AB">encode(sol)</span>**

👆 요기에서 **<span style="color:#6998AB">encode()</span>**에 대해서 알아보자!

![image-20211220170049617](/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220170049617.png)

✔︎ 인코딩을 하고 싶은 값을 파라미터로 넣으면 👉 JSON 형식의 새로운 값을 반환한다.

✔︎ Encodable 프로토콜을 준수해야 한다.

✔︎ 인코딩 중 규율을 따르지 않는  floating-point 값을 만나면 오류 👉 **<span style="color:#3E8E7E">`try`</span>**와 같이 사용한다. (throws: EncodingError.invalidValue)



### * Key 값이 다를 때 오류!

✔︎ 스펠링 오류: 이것은 회생불가.. 조심..!

✔︎ 서버의 키 값과 다른 키를 사용하는 경우

✔︎ 옵셔널 타입으로 선언하지 않은 키에 nil값이 올 경우

#### 내부에서 코드로 수정하는 방법...

iOS는 보통 camelCase를 사용한다. 만약 서버가 SnakeCase를 이용한다면 Xcode에서 변환하는 코드가 있다.

![image-20211220172430396](/Users/mimjoohehe/Library/Application Support/typora-user-images/image-20211220172430396.png)

✔︎ one_two_three 👉 oneTwoTree



🔖 참고

✦ SeSac 강의 자료

✦ https://babbab2.tistory.com/61



🔖
