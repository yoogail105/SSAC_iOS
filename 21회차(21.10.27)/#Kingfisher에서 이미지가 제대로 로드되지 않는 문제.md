# #Kingfisher에서 이미지가 제대로 로드되지 않는 문제


```swift
let url = URL(string: "https://example.com/image.png")
        cell.movieImage.kf.setImage(with: url)
```

<img width="441" alt="image" src="https://user-images.githubusercontent.com/53874628/139320887-19920ac5-d21c-4e85-82fa-b8bafa736721.png">

- 위에서 `url`은 사실 옵셔널이다❗️

→  `URL(string: "https://example.com/image.png")`이 `nil`이라면 별도의 처리가 필요하다.

→ `url = nil` 이라면, "background" 이미지가 뜨게 해준다.

```swift
if let url = URL(string: row.imageData) {
            cell.movieImage.kf.setImage(with: url)
        } else {
            cell.movieImage.image = UIImage(named: "background")
        }
```
