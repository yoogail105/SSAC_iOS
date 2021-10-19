# 하나의 UIView에 여러개 CollectionView 추가하기

- 똑같이 outlet등록, protocol연결, delegate연결, XIB 설정을 마친다.
- 그 후, CollectionView의 protocol이 선언되어있는 **extension에 `if조건문을 추가해서 구현한다!!`**

```swift
// 예를 들면, 이런 식이다ㅏ.
// CollectionViewCell 도 if문으로 처리해서 별도로 가져온다.

func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        
	if collectionView == tagCollectionVeiw {
		return 10
			} else {
		return 100
     }
}
```
