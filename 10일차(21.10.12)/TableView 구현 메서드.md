# TableVeiw 구현 메서드

### #indexPath 
```swift
indexPath.row: 셀의 위치(0부터 순서)
indexPath.section: 섹션의 위치(0부터 순서)
```
### #필수
#### 1. 셀의 갯수 `numberOfRowsInSection`

```swift  
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        <#code#>
    }
```

#### 2. 셀의 디자인 및 데이터 처리 `cellForRowAt`

```swift
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        <#code#>
    }
```

- 사실 이 두가지 메서드는 TableViewController.swift를 생성하면 자동으로 입력되어 있는 것이기도 하다.

### #옵션

#### 1. 셀의 높이 `heightForRowAt`

```swift
// 옵션이지만 지정하는 것이 좋음
    override func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        
        return indexPath.row == 0 ? 44 : 80
        //return indexPath.section == 0 ? 44 : 80
    }
```

#### 2. 섹션의 수 `numberOfSections`

: 디폴트 값은 1로, 지정해 주지 않으면 하나의 섹션이 만들어 진다.

```swift
    override func numberOfSections(in tableView: UITableView) -> Int {
        return 2
    }
```

#### 3. 섹션 타이틀 `titleForheaderInSectio`

```swift
override func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return "섹션 타이틀"
    }
```

#### 4. 스와이프 `canMoveRowAt`

```swift
    override func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
        if editingStyle == .delete {
            list.remove(at: indexPath.row)
            tableView.reloadData()
        }
    }
```
