## 1. URLRequest

- 서버로 네트워크 요청을 보내기 위한 URL, 로딩을 위해 사용되는 정책이 포함되어 있다.
- **어떤 HTTP Method(POST, PUT)**을 사용할 지, **어떤 데이터를 전달할 지(HTTP BODY),** **캐싱은 어떻게 할 지** 등 요청에 대한 정보를 담고 있다.

```swift
class APIService {
  			static func login(identifier: String, password: String) {

          let url = URL(string: "http://test.monocoding.com/auth/local")!
          var request = URLRequest(url: url)
          request.httpMethod = "POST"
          request.httpBody = "identifier=\(identifier)&password=\(password)".data(using: .utf8, allowLossyConversion: false)
        }
```

1. `let url = URL(string: "http://test.monocoding.com/auth/local")!`

   : url이 확실하니까 강제해제(!) 한다.

2. `request.httpMethod = "POST"`

   :HTTP Method를  `post` 로 설정한다.

3. `request.httpBody = "identifier=\(identifier)&password=\(password)".data(using: .utf8, allowLossyConversion: false)`

   : body는 form에 들어가는 공간으로,  여기에선느 identifier(id 혹은 email), password를 서버에 전달한다.

   1. string -> data로 반환
   2. dictionary -> JSONSerialization 또는 codable로 반환



🔖 참고

SeSAC 'iOS 개발자 데뷔 과정' 강의 자료
