# 고차함수**Higher-order function**

`map` `filter` `reduce`

- 고차함수는 많은 권한을 가지고 있는 **1급 객체**이다.
- 1급 객체의 특징 중 하나인 **매개변수와 반환값에 함수를 넣을 수 있다**는 것을 이용한다.

## `filter`

: 함수는 컨테이너 내부의 **값을 걸러서 새로운 컨테이너로 추출**

예를 들어서, 학점이 4.0이 넘는 학생을 뽑는다고 하자. 기존의 배열을 이용하면 **반복문**을 이용할 수 있다.

```swift
let student = [2.2, 5.5, 4.3, 3.3, 2.8]
var resultStudent: [Double] = []

for i in student {
    if i >= 4.0 {
        resultStudent.append(i)
    }
}

print(resultStudent)
```

이를 `filter`로 다시 식을 작성할 경우, 간단하게 표현이 가능하다.

```swift
student.filter { value in
	value >= 4.0
}
```

*`value`: student 배열 요소 하나하나

*결과를 담기 위한 배열을 선언하지도, 반복문을 통해 append해주지 않아도 된다는 장점이 있다.

→ 매개변수 대신에, 축약인자 `$0`를 이용하면 이를 더 간단하게 만들 수 있다.

```swift
let resultFilter = student.filter { $0 >= 4.0 }
```

*매개변수 value를 사용하지 않기 때문에 `value in` 통째로 생략해준다.

*이렇게 코드가 간단해지면, 속도와 효율성의 측면에서 월등하다.

### cf. 축약인자$0의 활용

기본적으로, dictionary는 순서가 없다. 하지만 `$0`을 이용해서 오름차순, 내림차순 등으로 배열의 순서를 지정할 수 있다.

```swift
let movieList = [
    "괴물": "박찬욱",
    "기생충": "봉준호",
    "인터스텔라": "크리스토퍼 놀란",
    "다리미": "안녕",
    "인셉션": "크리스토퍼 놀란",
    "옥자": "봉준호"
]
```

이 딕셔너리를 **내림차순**으로 정렬하려면 다음과 같이 쓸 수 있다.

```swift
let resultSort = movieList.sorted(by: { $0.key >  $1.key  } )
```

*`$0`.key >   `$1`.kyey

∙ 축약인자는 $0부터 순서대로 사용한다.

∙ 위의 식의 의미는 앞에있는 이자의 키값이, 뒤에있는 인자의 키값보다 **큰**것을 의미한다. 이때 값으로 오는 것들은 string이므로, 뒤로 갈수록 점점 key값이 작아지는, 즉 **내림차순**으로 정렬이 된다.

cf. `$0.key < $1.key`로 바꾸어주면, **오름차순**이 된다.

→ ***조금 더 줄여볼까?***

: 연산자를 사용할 수 있는 타입일 때에는 연산자만 남겨놓기OK

```swift
let resultSort = movieList.sorted(by:  >   } )
```

- 위의 movieLis에서 봉준호 감독의 영화를 찾아보자.

```swift
let movieResult = movieList.filter { $0.value == "봉준호"}
```

역시 축약인자 $0으로 key값을 별도의매개 변수 없이 나타내고, 값`$0.value`이 "봉준호"인지 비교한다. 기존처럼 for문을 사용한다면, 딕셔너리에 있는 튜플 하나가 "봉준호"인지 비교해야 하는 데 반해, 간단하게 작성되었다.

```swift
// cf. "봉준호"감독의 영화가 아닌 배열 작성
movieList.filter { $0.value != "봉준호" }
```

## `map`

: **기존 데이터를 변형(transform)하여 새로운 컨테이너를 생성**

1부터 9까지의 정수를 각각 2배를 한 새로운 배열을 만들고 싶다면,

배열의 각 요소를 돌면서 `*2`를 해주고, 이를 새로운 배열에 넣는다.

```swift
let number = [1, 2, 3, 4, 5, 6, 7, 8, 9]
var resultNumber: [Int] = []
for n in number {
    resultNumber.append(n * 2)
}
```

이때, `map`을 이용하면 기존의 배열을 수정하지 않고, 그리고 반복문을 돌지 않고도 새로운 배열을 출력할 수 있다.

```swift
let resultMap = nubmer.map { $0 * 2 }
```

또한 `filter`와 `map`을 함께 사용할 수 있다.

```swift
let movieResult = movieList.filter{ $0.value == "봉준호"}.map { $0.key }
```

위의 코드를 뜯어 보면,

1.  `movieList.filter{ $0.value == "봉준호"}`
    
    → valure값, 즉 영화 감독이 "봉준호"인 영화들을 뽑았다.
    
2. `.map { $0.key }`
    
    → "봉준호"감독의 영화 이름을 뽑아 새로운 배열로 만든다.
    
3. 즉, `print(movieResult)`의 결과는 다음과 같다.
    
    ```swift
    "["옥자", "기생충"]\n"
    ```
    

## `Reduce`

: 요소들을 합친 값을 사용하고자 할 때 쓰며, 컨테이너 내부의 **콘텐츠를 하나로 통합**한다.

한 학생의 시험 점수 총합을 구해보자. 기존의 방법은 역시 배열의 요소를 하나하나 돌며, 새로 선언한 변수 totalScore에 넣어 주었다.

```swift
let exam = [20,40,100,90,10,70]
var totalScore = 0

for i in exam {
    totalScore += i
}
```

`reduce`를 이용하면 이 과정을 간단하게 줄일 수 있다.

```swift
exam.reduce(0) { $0 + $1 }
```

`**reduce`** 에서 특히 주의할 점은, `초기화값`이다.

위의 코드에서는 초기화를 0으로 해 주어 exam 배열의 총합인 330이 된다.

하지만 만약 초기화를 100으로, 즉 `exam.reduce(100) { $0 + $1 }` 의 결과에서는 100에 exam배열의 총합을 더한 값인 430이 된다.

🔖 출처</br>

∙ SSAC iOS 개발자 데뷔 과정 강의와 강의자료</br>

∙ [https://yagom.github.io/swift_basic/contents/22_higher_order_function/](https://yagom.github.io/swift_basic/contents/22_higher_order_function/)</br>
