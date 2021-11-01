# #폰트 등록하기
<img width="730" alt="image" src="https://user-images.githubusercontent.com/53874628/139607494-c014c29c-1287-4c91-bafa-82de28a674be.png">

<img width="740" alt="image" src="https://user-images.githubusercontent.com/53874628/139607478-273261a1-a916-41df-a831-d6136d5e6ebb.png">

3. info.plist
<img width="427" alt="image" src="https://user-images.githubusercontent.com/53874628/139607540-ba65561f-4ebf-460f-b76b-c68e394766f9.png">
<img width="792" alt="image" src="https://user-images.githubusercontent.com/53874628/139607611-63e25a43-d015-4afd-9d5f-75d32895dd28.png">

폰트 이름 확인하기
<img width="261" alt="image" src="https://user-images.githubusercontent.com/53874628/139607773-8d3685ad-6ed5-4f02-b70d-e4598a4658f9.png">

```Swift
   for family in UIFont.familyNames {
            print(family)
            
            for sub in UIFont.fontNames(forFamilyName: family) {
                print("====> \(sub)")
            }
        }
```
```
 welcomeLabel.text = "HELLO WORLD! 반가워용"
        welcomeLabel.font = UIFont(name: "S-CoreDream-8Heavy", size: 14)
```

자주 사용하는 것익 때문에 -> Extension을 활용한다.
`UIFont+Extension.swift`
```Swift
import UIFont
extension UIFont {
    var mainBlack: UIFont {
        // 이 파일이 있는 것이 100% 확실하니까 ! 사용 ok
        return UIFont(name: "S-CoreDream-8Heavy", size: 14)!
    }
}
```

-> 사용
```Swift
  welcomeLabel.text = "HELLO WORLD! 반가워용"
        welcomeLabel.font = UIFont().mainBlack
```
