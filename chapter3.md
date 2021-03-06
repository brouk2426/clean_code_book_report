# 함수

## 작게만들어라!

함수는 작을 수록 좋다. 작게 만들었다면, 더 작게 만들어라.

함수의 들여쓰기는 1단, 내지 2단까지이다. 그 이상은 그 만큼 중첩구조가 커진다는 소리고, 이해하기 어려워 진다.

## 한 가지만 해라!

_<b>함수는 한 가지를 해야 한다. 그 한 가지를 잘 해야 한다. 그 한 가지만을 해야 한다.</b>_

1. 함수 안에서 추상화 수준이 하나인 단계만 수행한다면 그 함수는 한 가지 작업만 한다.

2. 함수 안에서 의미 있는 이름으로 다른 함수가 추출이 가능하다면, 그 함수는 여러 작업을 하는 셈이다.

## 함수 당 추상화 수준은 하나로!

함수 내 모든 문장의 추상화 수준이 동일해야 한다.

코드는 위에서 아래로 이야기처럼 읽혀야 좋다.
한 함수 다음에는 추상화 수준이 한 단계 낮은 함수가 온다.
즉, 위에서 아래로 프로그램을 읽으면 함수 추상화 수준이 한 단계씩 낮아진다.

함수의 추상화 수준을 하나로 두는 것은 상당히 어렵다.
하지만 반드시 기억해야할 규칙이다.
한 가지만 하는 함수라는 것을 기억해야 한다.

## Switch문

switch문은 작게 만들기 어렵다.
본질적으로 N가지를 처리하기 때문이다.
하지만 `polymorphism`을 이용해서 저차원 클래스에 숨기고 반복하지 않는 방법이 있다.

_<span style="color: gray">다형성의 예시로 들어준 코드는 어떤 부분에서 개선된건지 잘 이해를 못해서 공부를 더 해봐야 할 것 같다...</span>_

## 서술적인 이름을 사용하라

_<b>코드를 읽으면서 짐작했던 기능을 각 루틴이 그대로 수행한다면 깨끗한 코드라 불러도 되겠다.</b>_

한 가지만을 하는 작은 함수에 좋은 이름을 붙인다면 원칙을 달성함에 있어 기여했다고 볼 수 있다.

## 함수 인수

이상적인 인수 개수는 0개이다. 3개 이상은 가능한 피해야한다. 이유가 있다면 그래도 사용해도 안된다.

### 단항 함수

입력 인수를 변환하는 함수라면 변환 결과를 반환 값으로 돌려주어야 한다.

### 플래그 인수

플래그 인수는 추하다. 함수로 `boolean` 값이 넘어간다고 하는 순간부터 함수는 여러가지를 처리한다고 공표하는 행위이다.

### 이항 함수

자연적인 순서에 의한 인수는 불가피하다. 하지만 그러한 순서가 없는 인수의 나열은 오히려 혼란을 야기할 수 있다. 불가피하게 쓸 수 밖에 없을 때도 있겠지만 최대한 단항 함수로 바꾸도록 애써야한다. 메소드를 클래스의 구성원으로 만들던지, 구성원 변수로 사용한다던지.

### 삼항 함수

삼항 함수는 이항 함수를 보고 이해할때 보다 훨씬 더 어렵다.
신중히 고려해야 한다.

### 인수 객체

인수가 2~3개 필요하다면 일부를 독자적인 클래스 변수로 선언할 가능성도 짚어본다. 눈속임이라고 보일지도 모르지만, 하나로 묶으면서 하나의 개념이 되기 때문이다.

### 인수 목록

가변 인수를 사용해야 할 때도 있다. 하지만 이또한 삼항 함수를 넘어 간다면 문제가 많아진다.

### 동사와 키워드

예시로 단항 함수의 경우 함수가 동사, 인수가 명사의 형태를 띄운다면 명확하게 표현된다. 나아가 삼항 함수의 경우 함수의 이름에 인수의 이름(키워드)을 넣게 된다면 더 명확하게 이름을 지을 수 있다.

### 부수효과를 일으키지마라.

남몰래 부수효과를 일으키는 건 교활하고 해로운 거짓말이다. `temporal coupling`, `order dependency`를 초래하게 된다. 다른 행위를 해야한다면 한 가지만 한다는 규칙을 위반하더라도 함수 이름에 명확히 표현해야한다.

## 명령과 조회를 분리하라.

뭔가를 수행하던지, 뭔가에 답하던지 둘중 하나만 해야 한다.
객체를 변경하던지, 객체 정보를 반환 하던지.

## 오류 코드보다 예외를 사용해라

예외 처리를 하면 오류 처리 코드가 원래 코드에서 분리되어 깔끔 해진다.

## Try/Catch 블록 뽑아내기

try/catch 블록은 코드 구조에 혼란을 일으킬 수 있다. 블록의 코드들은 별도의 함수로 뽑아내는 것이 좋다.

### 오류 처리도 한 가지 작업이다.

오류 처리를 하는 함수는 오류 처리만 하는 것이 마땅하다.

## 반복하지 마라!

중복은 소프트웨어에서 악의 근원이다.
RDB의 정규화, 객체지향의 부모 클래스 등등 중복을 제거하려는 지속적인 노력이 보이고 있다.

## 함수를 어떻게 짜죠?

글짓기와 똑같다. 생각을 기록하고 읽기 좋게 다듬는다. 초안은 서투르고 어수선하다. 원하는 대로 읽힐 때까지 다듬고 다듬는다.
