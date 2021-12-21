# Codable

## Codable

`codable`? 



✔︎ **JSON과 같은 외부 표현을 <span style="color:#3E8E7E">간편하고, 쉽게 Encoding / Decoding</span>  할 수 있게 해 주는 프로토콜.**

✔︎ 디스크에 데이터를 저장, 네트워크 연결 등을 통한 API 통신 등의 작업 등에서는 데이터가 저장되는 동안 중간 형식(intermediate format)으로 데이터를 인코딩/디코딩 해야 하는 경우가 많다.

​	👉 이때 Swift 표준 라이브러리에서는 Codable을 통한 표준화된 접근 방식을 제공한다!



- **<span style="color:#3E8E7E">`Encoding`</span> ?**

​	: struct, class, enum 등의 인스턴스를 **JSON형태의 데이터로!**

- **<span style="color:#3E8E7E">`Decoding`</span> ?**

​	: JSON형태의 데이터를 struct, class, enum 등의 **인스턴스로!**



Xcode에서 Codable 정의를 살펴보면,</br>
<img width="657" alt="image-20211220152919834" src="https://user-images.githubusercontent.com/53874628/146882918-5cec656b-6fac-43ed-8905-b646e6aee957.png">

- **Codable**은 **Encodable, Decodable 프로토콜**의 *typealias*이다.
- 따라서 Codable은 양방향 인코딩/디코딩을 을 지원한다.
- 만약 양방향을 지원하지 않는 경우라면 **Decodable, Encodable **중에 **독립적**으로 채택해서 사용할 수 있다.
- Codable은 struct, class, enum 등 모두가 채택할 수 있으며, 보통 struct를 선호한다.



🔖 참고

✦ SeSac 강의 자료

✦ https://babbab2.tistory.com/61

