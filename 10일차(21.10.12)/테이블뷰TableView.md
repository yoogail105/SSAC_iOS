# #TableViewController

**`@MainActor class UITableView : UIScrollView`**

### 1. 테이블뷰의 필요성
![image](https://user-images.githubusercontent.com/53874628/136943248-0a5f4d6d-b9aa-44f9-a52f-c84795fbd082.png)

내가 매일 사용하는 어플들을 보면 테이블뷰를 이용하고 있는 것을 알 수 있다.<br/>
웹툰 어플의 한 화를 표시하는 박스, 그리고 친구 목록 한 명의 정보를 담은 박스들이 테이블뷰로 이루어져 있다.<br/>
나는 친구 목록에 30명만 표시 되어도 되지만, 인싸들은 3000명의 연락처를 저장했을 수도 있는데,,<br/>
이럴 때 테이블뷰를 이용하지 않고, 하나하나를 만든다면 너무 많은 outlet들이 필요해 진다.<br/>
데이터가 너무 많을 경우 각각을 따로 등록하지 않고, 하나의 틀을 만들어서 내용만 바꿔 끼우는 역할을 하는 것이 테이블뷰라고 할 수 있다.<br/>

```swift
# 테이블 뷰의 필요성
1. 많은 뷰 객체
2. 반복적인 디자인과 코드
3. 어려운 스크롤 구현
```

### 2. 테이블 뷰의 구성 및 특징
![Untitled](https://user-images.githubusercontent.com/53874628/136943513-e989ec8e-0776-4fe7-99b0-cd6aabbb1dc6.png)
- Xcode에서 `UITableViewController`를 가져오면, viewController와 table view가 포함된 씬이 생성된다.
- TableView는 View와 다르게, `루트뷰가 테이블뷰`로 구성되어 있다.
- View Controller를 상속받고 있기 때문에, 그 기능을 사용할 수 있다.
- 하나의 `Cell`만을 구성해서, 코드를 통해 여러개로 복제하여 사용한다.
    
    (cell의 갯수에 따라서 계속 스크롤 되며, 무한 스크롤 구현이 가능하다.)
    
![Untitled-2](https://user-images.githubusercontent.com/53874628/136943518-900ef68a-5f80-4011-89bb-f6f055b246d1.png)
- 기본적으로는 위와 같이 간단한 텍스트와 이미지로 구성되어 있지만, 커스텀을 통해 다양하게 디자인을 할 수 있다.
- header와 footer를 통해 추가적인 정보를 입력할 수 있다.
- `data-driven`
    1. 테이블 뷰는 우리가 제공한 데이터 소스 객체(데이터베이스)로부터 생성된다.
    2. 데이터소스오브젝트는 우리가 만드는 앱의 데이터와 테이블의 셀을 관리한다.
    3. 그런데 만약 그 내용이 변하지 않고 **고정**되어 있다면, **storyboard**로 설계할 수도 있다.

#### 출처
    - SSAC iOS 강의 자료
    - [https://developer.apple.com/documentation/uikit/uitableview](https://developer.apple.com/documentation/uikit/uitableview)
