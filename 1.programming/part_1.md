# Principles of Programming Part 1

## 1. 프로그래밍 기본 부품과 조합 (elements & compound)

### 1.1. 기본 부품 (primitives)
- Scheme의 기본 타입: N,R,B,String,Symbol
- 실행(evaluation, semantics): -1.2e2는 -1.2 X 10^2, #t는 참, 'snow는 "snow"라는 심볼 등.

### 1.2. 식을 조합하는 방법
    P  ::=  E               program  (program == expression)
    E  ::=  c               constant (expression == constant)
        |   x               name                (or variable)
        |   (if E E E)      conditional
        |   (cons E E)      pair
        |   (car E)         selection
        |   (cdr E)         selection
        |   (lambda (x*) E) function
        |   (E E*)          application

- 재귀적(inductive, recursive): 
    - 만들 수 있는 식은 무한히 많음
    - 식안에 임의의 식들을 맘껏 조합할 수 있음
- 조합식의 실행(semantics)은 어떻게 될까? 그 실행을 머릿속에 그려야. (e.g. JAVA documentation: 이렇게 쓰면 이런식으로 실행됩니다.)

### 1.3. 프로그램 식의 실행과정
    1. 주어진 프로그램 식을 읽고 (read)
    2. 그 식을 계산하고 (evaluate)
        - 계산중에 컴퓨터 메모리와 시간 소모
        - 계산중에 입출력이 있으면 입출력을 수행
    3. 최종 계산 결과가 있으면 화면에 프린트한다 (print)   

###### 주의
    - 식의 실행 규칙(rule of evaluation, semantics): 명확히 정의됨 (C같은 경우는 명확히 정의되지 않은 구석이 있으며, 이는 컴파일러가 마음대로 번역한다고함)
    - 프로그래머는 이것을 이해해야 의도한 프로그램을 작성할 수 있음
    - 제대로 실행될 수 없는 멀쩡한 식들이 많음 e.g (+ #f 3)

### 1.4. 식의 실행규칙(rule of evaluation, semantics)
실행 규칙. 각 식의 종류에 따라서:
- c 일때: constant일때 그 값을 그대로 이해하는 것.
- x 일때: x = 'Jane' table을 컴퓨터가 기억하고, x를 만났을때 Jane.
- (if E E E) 일때: 첫번째 E계산 후 true면 두번째 E계산, false면 세번째 E계산
- (cons E E) 일때: 두 E를 계산 후 짝을 만듦
- (car E) 일때: E를 계산한후 그 E는 pair여야 하며, pair의 첫번째 element를 return
- (cdr E) 일때: 두번째 element
- (lambda (x*) E) 일때: (x*)는 argument, E는 body (lambda (i) (*i i))
- (E E*) 일때: ((lambda (i) (*i i)) 1 3) 3을 리턴.

###### 주의
    - 생긴게 옳다고 모두 제대로 실행되는 게 아님
    - 부품식들의 계산결과의 타입이 일치해야
    - 이름의 사용, 이름의 유효범위(scope)

### 1.5. 프로그램식 조합방식의 원리
🌟 모든 프로그래밍 언어에는 각 타입마다 그 타입의 값을 *만드는 식*과 *사용하는 식*을 구성하는 방법이 제공된다. (만들기 Introduction + 사용하기 Elimination)

## 2. 이름짓기 (binding, declaration, definition)

### 2.1. 이름짓기 (binding, declaration, definition)
🌟 이름 짓기는 *속 내용 감추기* (*abstraction*)의 첫 스텝: 이름을 지으면 지칭하는 대상(속내용) 대신에 그 이름을 사용

- 이름 지을 수 있는 대상:
    - 프로그램에서 다룰 수 있는 모든 값 (좋은 language 라면)
- 이름의 유효범위 (scope)가 한정됨. 따라서,
    - 이름 재사용 가능: 재사용 불가능하면 이름 짓느라 머리아프겠지...
    - 전체 프로그램의 모든 이름을 외울 필요 없음
    - 이름이 필요한 곳에만 알려짐
- 이름의 유효범위(scope)는 쉽게 결정됨    

### 2.2. 이름의 유효범위(scope) 결정
프로그램 텍스트에서 쉽게 결정됨 (lexical scoping, static scoping)

## 3. 재귀와 고차함수 (recursion & higher-order functions)
## 4. 프로그램의 계산복잡도 (program complexity)
## 5. 타입으로 정리하기 (types & typeful programming)
## 6. 맞는 프로그램인지 확인하기 (program correctness)