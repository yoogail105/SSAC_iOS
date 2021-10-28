# RestAPI
: Representational State Transfer

- 네트워크를 통해서 핵심 컨텐츠와 기능을 활용할 수 있도록 제공되는 인터페이스, 아키텍쳐 스타일

- `자원(Resource)`를 중심으로 `엔드포인트(URI)`를 생성하고
    
    `HTTP method(GET, POST, PUT, DELETE)`를 통해 동작을 수행
    
    * **`자원`**: 서버에서 데이터를 제공해주는 모든 요소(이미지, 텍스트 등)
    * **`엔드포인트(URI)`**: Uniform Resource Identifiers
   
      ∙ 모든 자원은 고유한 URI를 가지고 있다
      
      ∙ HTTP API의 엔드포인트는, HTTP메소드와 URI를 사용하여, **API가 어떤한 동작을 수행하는 API인지 표현**한다.
    
     * **HTTP** 기반으로 동작이 이루어진다.
     * 데이터의 포맷: **XML, JSON**

cf. RESTful API

### REST API 6원칙

1. Uniform Interface

   - 모든 자원은 식별 가능해야 한다.
    
    (ex. 모든 이미지의 고유한 주소값 O)
    
   - HTTP method를 통해서 자원을 조작해야 한다.
    
    : 요청해야 → 응답한다.
    
2. Stateless
    
    : 무상태(클라이언트의 상태 남아있지 않음)
    
3. Cacheable
    
    : 캐시를 처리할 수 있다.
    
    일정시간동안의 캐시를 만들어 놓았다가, 많은 사용자들이 한번에 요청하면 그 영역에서 전달
    
4. Self-Descriptiveness
    
    : API 메세지만으로 무엇을 의미하는지 유추할 수 있어야 한다.(명확)
    
5. Client - Server
6. 계층형 구조

### 장점

- 웹의 장점을 최대한 활용한 아키텍처
- HTTP(S)에서 손 쉽게 구현
- 특정 언어나 기술에 종속되지 않음
    
    : 다양한 플랫폼에서 다룰 수 있다.
    
- API 의도 직관적 파악

### 단점

- `OverFetching`: 내가 필요한 것보다 훨씬 많은 정보를 받는다.
- `Underfetching`: 너무 세분화 되어 있을 때에는 여러번 호출해야 한다.
- `Endpoind`: 서비스가 커질수록 거쳐 가야하는 endpoint들이 늘어난다.
