# #Decodable

✔︎ JSON 등의 외부 형식의 데이터를 내부의 원하는 인스턴스로 변환한다.

✔︎ Struct, Enum, Class 에서 모두 채택할 수 있다.

✔︎ 여러 데이터 중에서 Key의 일부를 디코딩하지 않는 것 OK

​	👉 But, Key값이 동일하지 않거나 호환되지 않는 형식으로 저장된 경우에는 디코딩에 실패하기 때문에 별도 처리가 필요하다.

  - 스펠링 오류

  - 서버의 키 값과 다른 키를 사용하는 경우

  - 옵셔널 타입으로 선언하지 않은 키에 nil값이 올 경우

  - ...

    👉 이렇게 별도의 처리가 필요한 경우에는 `init`을 모델 내에서 생성하여 구현한다.






<br/>
## CodingKey

- 원하는 키로 모델을 생성하고 싶거나, 기본적으로 제공해주는 디코딩 전략으로는 원하는 형태를 얻기 어렵다면, 커스텀키를 생성

- 이때, CodingKey프로토콜로 인코딩과 디코딩을 할 수 있는 키로 사용할 수 있다.

- `CodingKeys`: 

  - 모든 속성이 열거형 CodingKeys에 포함되어야 한다.
  - 커스텀 키로 사용하지 않더라도, 포함해야 한다.
  - 커스텀 키로 사용하지 않는 경우에는, 열거형의 속성대로 원래의 이름 그대로 rawValue로 들어간다.

  ```swift
  struct Beer: Decodable {
      let id: Int
      let name, tagline, description, imageURL: String
      let foodPairing: [String]
      
      
      enum CodingKeys: String, CodingKey {
          case imageURL = "image_url"
          case foodPairing = "food_pairing"
          case id, name, tagline, description
      }
  }
  ```
<br/>

## init(from decoder: Decoder) & decodeIfPresent

✔︎ 서버에서 받은 값을 그대로 사용하지 않고, 변형해서 사용하고 싶은 경우에 사용






<br/><br/>
🔖 참고

✦ SeSAC iOS 개발자 데뷔과정 강의자료
