# CollectionViewCell에 버튼 추가

### 1. 하트버튼 클릭에 대한 입력 받기

- `addTarget`
    
    : Associates a target object and action method with the control.
    

```swift
// heartButton
cell.heartButton.tag = indexPath.item
cell.heartButton.addTarget(self, action: #selector(heartButtonClicked(selectedButton: )),for:.touchUpInside)
```

→ viewDidLoad()에 heartButtonClicked의 함수 적어준다.

```swift
@objc func heartButtonClicked(selectedButton: UIButton) {
     print("\(selectedButton.tag) 버튼 클릭!")
           
        }
```

### 2. 클릭 여부에 따라서 색상 변경하기

- heartButton.tag를 이용
- 한 번 누르면 true, 다시 한 번 더 누르면 false

1. heartButton 갯수만큼의 bool값을 담은 배열 선언

```swift
var heartArray = Array(repeating: false, count: 100)
```

2. heartButton이 들어있는 dequeueReusableCell이 선언되어 있는 부분에서 → indexPath.item의 정보를 가져온다.(true/false)
    
    → 삼항 연산자를 통해서 true이면 fill, false이면 빈 하트를 출력
    

```swift
var item = heartArray[indexPath.item]

let image = item == true ? UIImage(systemName: "heart.fill") : UIImage(systemName: "heart")
//let image = item ? UIImage(systemName: "heart.fill") : UIImage(systemName: "heart")

cell.heartButton.setImage(image, for: .normal)
```

3. 클릭에 따라서 true↔false 바뀌도록 배열 값 변경하기
    
    → 특정 버튼 selectedButton.tag를 클릭하면, !를 통해 값 반전
    

```swift
@objc func heartButtonClicked(selectedButton: UIButton) {
		print("\(selectedButton.tag) 버튼 클릭!")
		heartArray[selectedButton.tag] = !heartArray[selectedButton.tag]
		colorCollectionView.reloadData()
}
```

**`필요한 셀만 리로드`**

```swift
colorCollectionView.reloadItems(at: [IndexPath(item: selectedButton.tag, section: 0)])
```
