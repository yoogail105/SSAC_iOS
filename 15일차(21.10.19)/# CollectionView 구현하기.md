# CollectionView 구현하기

`TableView`의 구성과 굉장히 유사하다. 단,

```swift
tableView ⇒ CollectionView
row → item
```

### CollectionView만 따로 extension으로 가져와준다

```swift
// 1.CollectionView Outlet 연결
@IBOutlet weak var ColorCollectionView: UICollectionView!
```

```swift
// 2. CollectionView Protocol
extension MainCollectionViewController: UICollectionViewDelegate, UICollectionViewDataSource {
    func collectionView(_
```

```swift
// 3. protocol 연결
override func viewDidLoad() {
        super.viewDidLoad()
  
        colorCollectionView.delegate = self
        colorCollectionView.dataSource = self
        
    }
```

→ 여기에서 오류가 나는 것은 CollectionView의 필수 요소들을 설정해 주지 않아서 그렇다!

```swift
extension ColorCollectionViewController: UICollectionViewDelegate, UICollectionViewDataSource {
    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return 100
    }
    
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        
        guard let cell = collectionView.dequeueReusableCell(withReuseIdentifier: ColorCollectionViewCell.identifier, for: indexPath) as? ColorCollectionViewCell else {
            return UICollectionViewCell()
        }
        
        return cell
    }

}
```

```swift
// 4. XIB 처리
let nibName = UINib(nibName: ColorCollectionViewCell.identifier, bundle: nil)
//위의 것을 어디에 등록해줄 거냐면!
colorCollectionView.register(nibName, forCellWithReuseIdentifier: ColorCollectionViewCell.identifier)
```
