# #Storyboard reference

## 1. Storyboard Reference ?

스토리보드는 뷰 컨트롤러 간의 관계와 그 안의 UI 구성을 한 눈에 파악할 수 있어 용이하다.

하지만,

- 협업을 하게 되면 Git Merge 시 스토리보드에서 **충돌이 발생**하고,
- 하나의 스토리보드에 여러 개의 view Controller가 추가 되면 **Xcode의 퍼포먼스가 심하게 저하된다.**

이런 문제를 해결하기 위해서는

→ 100% 코드 개발

→ One Storyboard - One ViewController : Storyboard 나누기

의 두 가지의 방법 중 선택할 수 있다.

* **`Storyboard Reference는 스토리보드를 나누는 데에 사용한다.`**

## 2. Storyboard Reference 사용하기

- storyboard에서 label을 추가하듯이 추가해준다.
    <img width="677" alt="스크린샷 2021-10-18 오후 11 57 01" src="https://user-images.githubusercontent.com/53874628/137756415-60f51df8-c33c-4ec2-8039-4ea4e96b71f5.png"></br>

- 인스펙터에서 연결해줄 스토리보드를 선택한다.<br>
    <img width="512" alt="스크린샷 2021-10-18 오후 11 57 20" src="https://user-images.githubusercontent.com/53874628/137756387-994858d7-70b6-4a84-874a-48a6a35d71ae.png">

→ 오잉 근데 안된다..?이따가 다시 봐야겠따..
