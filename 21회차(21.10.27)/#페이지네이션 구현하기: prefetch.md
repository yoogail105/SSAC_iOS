# #페이지네이션 구현하기: prefetch

### 1. 작동 원리 ?

```swift
let url = "https://openapi.naver.com/v1/search/movie.json?query=\(query)&display=10&start=1"
```

위의 코드에서, `display=10&start=1`을 주목하자.

한 번에 10개의 셀`display=10`을 준비해서 정보를 보여준다고 했을 때, 시작점`start`가 1에서 11로, 11에서 21로 ... 바뀌어야 한다!

→ **sartPage 변수로 관리**


### 2. **`UITableViewDataSourcePrefetching`**

```swift
class SearchViewController: UIViewController, UITableViewDataSourcePrefetching {
}
```

- 용량이 큰 데이터를 다운받을 때, 시간이 걸리니까 미리 데이터를 다운 받아 놓는 것
- `cellForRowAt`보다 먼저 호출이 된다.
- **다운로드를 받을 준비를 하다가도, 취소할 수 있는 기능**이 있다!
    
    (사용자가 스크롤을 너무 빨리 내려서 화면에 굳이 표시되지 않아도 될 때 사용한다.)
    

✔︎ **protocol**이므로 →viewDidLoad()에 delegate 위임 해주기: `tableVeiw.prefetchDataSource = self`

### 2-1. `필수 메서드` 있다!

<img width="497" alt="image" src="https://user-images.githubusercontent.com/53874628/139320525-3499da72-fdda-4bb1-966a-cda27119e10a.png">

1. **필수)** 셀이 화면에 보이기 전에 필요한 리소스를 미리 다운 받는 기능: **`prefetchRowsAt`**

```swift
func tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) {
        for indexPath in indexPaths {
            if movieData.count - 1 == indexPath.row {
                startPage += 10
                fetchMovieData()
                print("prefetch: \(indexPath)")
            }
        }
    }
```

2. 옵션) 데이터 다운을 취소하는 기능: **`cancelPrefetchingForRowsAt`**

```swift
 // 옵션: 취소
    func tableView(_ tableView: UITableView, cancelPrefetchingForRowsAt indexPaths: [IndexPath]) {
            print("취소: \(indexPaths)")
    }
```

**→ 스크롤을 재빠르게 내리면, 데이터 로드가 취소된 것을 확인할 수 있다.**

<img width="324" alt="image" src="https://user-images.githubusercontent.com/53874628/139320571-c226ff08-f445-4543-a0ff-2947d0643d38.png">
