# # collection view

<img width="660" alt="image" src="https://user-images.githubusercontent.com/53874628/137926011-538f46c2-7bee-4c5e-b077-dac5d2cc209d.png">

### Collection View와 Table View의 차이

- TableView: 수직만 고려
- CollectionView: 수평, 수직을 모두 고려

## CollectionView 고려해야할 지점

1. `여백`(컬렉션 뷰의 위,아래, 양 옆 여백 4가지)
    
    → **스크롤을 하는 도중 사용할 수 있는 여백이다!**
    
    → 보통 사용자가 편하도록 스크롤을 할 수 있는 공간을 준다.
    
2. 셀과 셀 사이의 간격: `상하`
3. 셀과 셀 사이의 간격: `좌우`

cf. `셀의 크기:` 위의 여백들을 다 빼고 디바이스의 너비에서 n을 나누는 방법

디바이스의 너비에 따라서 달라지기 때문에, 고정으로 사용하는 경우는 많지 않다.

## CollectionView Inspector

- Layout: Flow: 모든 셀의 크기가 같음
- 수평스크롤: 셀이 계속 수직으로 쌓이다가 자리가 없으면 그 때 옆으로 스크롤
- Estimate Size: `none`
- Secion Insets의 여백은 스크롤이 가능한 영역이다!
