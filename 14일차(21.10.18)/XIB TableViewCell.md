# #XIB TableViewCell

- 똑같은 디자인을 반복적으로 사용할 때 → `**module**`로 작업(XIB)

### 1. XIB TableViewCell 생성하기

- UITableViewCell Custom Class 파일 만들 때
    - [ ]  `**Also create XIB file**` chcek ✔︎
- `.swift`, `.xib` 파일 두 개가 동시에 생성된다.
<img width="727" alt="스크린샷 2021-10-18 오후 11 53 30" src="https://user-images.githubusercontent.com/53874628/137755702-2bbca041-deb9-4bfc-962a-0a0088a7562c.png">

### 2. Cell identifier 설정

- 오른쪽의 identity inspector에서 class를 연결해 주지 않아도 된다. (자동연결)
- 그러나, `**cell idnetifier**`는 설정해 주어야 한다!
<img width="535" alt="스크린샷 2021-10-18 오후 11 54 23" src="https://user-images.githubusercontent.com/53874628/137755824-ced27442-ab62-442a-9cf7-04d203812683.png">



### 3. Register Cell

- 테이블 뷰에서 셀을 사용하겠다는 코드 작성하기
    
    ```swift
    class settingViewController: UIViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            
            // extension 연결
            settingTableView.delegate = self
            settingTableView.dataSource = self<img width="543" alt="스크린샷 2021-10-18 오후 11 53 36" src="https://user-images.githubusercontent.com/53874628/137755662-85e48165-7454-47b3-b5f3-df17a39388a1.png">

            
            // MARK: - tableviewcell을 xib로 사용할 경우
            let nibName = UINib(nibName: DefaultTableViewCell.idnetifier, bundle: nil)
            settingTableView.register(nibName, forCellReuseIdentifier: DefaultTableViewCell.idnetifier) 
        }
    ```
