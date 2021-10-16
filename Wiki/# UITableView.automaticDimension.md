# # UITableView.automaticDimension

### 1. `automaticDimension`

```swift
  override func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {

          return UITableView.automaticDimension
        
    }
```
- 주어진 row의 높이를 자동으로 계산해서 반환
<br>

### 2. `estimatedRowHeight`

- row의 높이에 대한 nonnegative한 추청값은 테이블뷰를 로드하는 성능을 향상 시킨다
- 만약 테이블뷰의 높이가 다양하다면 테이블 뷰가 로드될 때 많은 계산이 필요
- 추정은 로드타임부터 스크롤을 하는 타임까지 계산하는 시간을 미루게 해 준다.
<br>

- default: automaticDimension
    : 테이블 뷰가 예상 높이 선택
- estimaedRowHeight을 0으로 셋팅하면 높이를 예상할 수 없음
    → 각 셀에 대한 실제 높이를 요구한다.
- self-sizing cells 이용하고 싶다면,
    `**estimaedRowHeight ≠ 0**`    
<br>

### → `estimatedHeightForRowAt`

```swift
override func tableView(_ tableView: UITableView, estimatedHeightForRowAt indexPath: IndexPath) -> CGFloat {

        return UITableView.automaticDimension
}
```
- 예상값 없으면 automaticDimension 반환
<br>

cf. 특정 섹션만 고정하기
 → `indexPath.row` 활용
 <br>
 <br>

🔖 참고

∙[https://bannavi.tistory.com/306](https://bannavi.tistory.com/306)<br>
[apple Documentation]<br>
∙[automaticDimension](https://developer.apple.com/documentation/uikit/uitableview/1614961-automaticdimension/)<br>
∙[estimatedRowHeight](https://developer.apple.com/documentation/uikit/uitableview/1614925-estimatedrowheight/)<br>
∙[ableView(_:estimatedHeightForRowAt:)](https://developer.apple.com/documentation/uikit/uitableviewdelegate/1614926-tableview/)<br>
