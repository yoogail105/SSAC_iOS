# CollectionView Layout: Flow Layout

- viewDidLoad()에 FlowLayout을 사용한다고 선언해 준다.

```swift
let  layout = UICollectionViewFlowLayout()
        layout.itemSize = CGSize(width: 100,height: 100)
        colorCollectionView.collectionViewLayout = layout                                                                                                                                                                                                    
```

- 하나의 cell의 사이즈를 화면의 크기에 맞추기 위해서 수식을 이용.
    
    but.itemSize의 형식이 `CGSize` -> spacing의 타입 명시한다(타입어노테이션)
    

```swift
let  layout = UICollectionViewFlowLayout()
let spacing: CGFloat = 20
let width = UIScreen.main.bounds.width - (spacing * 4)
layout.itemSize = CGSize(width: width / 3,height: (width / 3) * 1.2)
layout.sectionInset = UIEdgeInsets(top: spacing, left: spacing, bottom: spacing, right: spacing )
// 줄 사이 간격
layout.minimumLineSpacing = spacing
// 한 줄에서 item과 item간의 간격
layout.minimumInteritemSpacing = spacing
layout.scrollDirection = .vertical

colorCollectionView.collectionViewLayout = layout
```
