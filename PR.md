## 📌 과제 설명
### 요구사항
- 객체지향적인 코드로 계산기 구현하기
    - [x]  더하기
    - [x]  빼기
    - [x]  곱하기
    - [x]  나누기
    - [x]  우선순위(사칙연산)
- [x]  테스트 코드 구현하기
- [x]  계산 이력을 맵으로 데이터 저장기능 만들기
    - 애플리케이션이 동작하는 동안 데이터베이스 외에 데이터를 저장할 수 있는 방법을 고안해보세요.
- (선택) 정규식 사용

사칙연산 결과가 최대 소수 2자리까지 나올 수 있게 구현하였습니다.
Test 코드는 JUnit 을 이용하여 작성하였습니다.
정규식은 사용하지 않았습니다.

## 👩‍💻 요구 사항과 구현 내용
### commit completed version
엔티티, 레포지토리, 서비스, 테스트 부분의 코드를 제가 한번에 commit 해서 올렸습니다.. 너무 죄송합니다... 다음부터는 기능별로 쪼개서 올리겠습니다.

엔티티는 사용자가 작성하는 수식과 수식의 결과값을 가지고 있습니다.
레포지토리는 출력 순서를 보장하기 위해 LinkedHashMap 을 사용하여 구현하였습니다.

서비스는 validation 부분과 calculate 부분이 있습니다.
- validation 부분에서 시스템 에러가 발생할 수 있는 모든 부분들을 처리해 주었습니다
- case0 : 초기 입력 숫자 1인지 2인지 체크
- case0 : 띄어쓰기 안된경우 체크
- case1 : 숫자가 입력되었는지 체크
- case2 : 사칙 연산 문자열이 들어왔는지 체크
- case3 : 마지막에 연산자로 끝나는 경우 오류 발생으로 종료시켜버린다.(인덱식한 문제 합이 짝수)(1+2+3+ -> 인경우 index==6)

- calculate 부분은 사칙연산 계산 로직이 있습니다.

### MainClass 를 MainApplication 과 MainService 로 분리하여 책임분리
스프링 처럼 실행 부분은 실행 로직만 존재하게 하기 위해 클래스를 책임에 맞게 분리하였습니다.

### 팩토리 패턴 적용(AppConfig 로 Repository 변경 시 의존성 관리)
Repository 를 Interface 를 통해 변경 가능하게 로직을 작성하였기 때문에 의존성 관리를 AppConfig 로 수행하기 위해 팩토리 패턴을 적용시켜 보았습니다.


## ✅ 피드백 반영사항

## ✅ PR 포인트 & 궁금한 점
- 다음부터는 commit 을 잘게 쪼개서 올리겠습니다. 죄송합니다...
- CalculationService 클래스에서 계산로직 작성에 있어서 if 문속에 if 문이 반복적으로 사용되는 코드는 좋지 않은 코드인지, 그리고 그런 로직은 어떠한 방식으로 작성하는게 좋은지 궁금합니다.
- 테스트 코드 작성을 자주 하지 않았는데 제가한 방식의 테스트 코드 작성이 올바른지 궁금합니다.


