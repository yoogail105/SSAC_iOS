## Operator

- Obserbable<Int>.just(1)
- Obserbable<Int>.of(1)
  - 여러 개 가능
- Obserbable<Int>.from([1,2,3])
  - 반드시 Array
- Obserbable<Void>.empty()
  - 아무런 이벤트도 방출하지 않음: completed()만 방출
- Obserbable<Void>.never()
  - 아무런 이벤트도 방출하지 않음: debug를 통해서만 제대로 구독되고 있는지 확인 가능
- Obserbable.range(satrt:1, count: 9)
  - start, count 값을 통해서 순차적으로 하나씩 방출

## Subscribe

- .subcribe {}
  - 구독하지 않으면 소용이 없다!
  - 구독한 이후의 옵저버블만 유효하다.

## Dispose

- let disposeBag = DisposeBag()

  .disposed(by: disposeBag)

  - 옵져버블을 생성한 후에는, 반드시 disposed를 해 주어서 메모리가 누수되지 않도록 한다.

## Create

- Observable.create {}
  - 이벤트를 각각 방출하는 Observable을 이용해서 옵져버블 시퀀스를 만든다.

- Observable.deferred {}
  - 옵저버블 팩토리를 이용해서 옵저버블 시퀀스를 만든다.
  - 실제 구독이 일어나는 시점에, 실제 Observable을 만든다.

