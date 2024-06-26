<Day03 - 0321>
<Javascript 연산자>

# 연산자

    - 항 : 연산에 사용되는 값
        연산에 사용되는 값의 갯수
            1 : 단항 연산
            2 : 이항 연산
            3 : 삼항 연산

    - 연산자 : 연산에 사용되는 기호

1. 산술연산자
   - ( + - _ / % ) 더하기(+), 빼기(-), 곱하기(_), 나누기(/), 나머지(%)
   - % : 나머지 연산자 : 나머지가 나누는 수보다 작은 수가 반복되어 나옴.
     (3으로 나누면 나머지는 0~2 반복 - 균등배분)
   - - : 숫자 + 숫자 => 숫자
       문자 + 문자 or 다른 자료형 => 문자 결합 (abctrue, abc1000)

- 연산자의 우선순위. \* / % > + -
- (..) : 소괄호 사용 시 적용 우선순위가 가장 높음. 연산자의 우선순위 강제 적용

2. 문자 결합 연산자

- 수치를 연산하는 것이 아닌 문자를 결합하는 것
- 여러개의 문자를 하나의 문자형 데이터로 결합할 때 사용
- 더하기에 피연산자로 문자형 데이터가 한 개라도 포함되어 있으면 다른 피연산자의 데이터는 자동으로 문자형 데이터로 형 변환되고 문자 결합이 이루어져 하나의 문자형 데이터로 반환

  (예시)
  "Text1 " + "Text2" = "Text1 Text2";
  "100" + 200 = 100200;
  100 + "200" = 100200;

3. 대입연산자
   - =
     A = B
     A = 1 + 2

- 연산된 데이터를 변수에 저장할 때 사용
  - 오른쪽에서 일어난 연산 결과값을 왼쪽 변수에 저장
  - 연산의 우선순위가 가장 낮음

* 복합대입연산자 : 산술연산자( + - _ / % ) + 대입(=) 결합된 연산자
  연산자를 결합하여 짧게 쓸 수 있음
  A += B A = A + B
  A _= B A = A \* B
  A /= B A = A / B
  A %= B A = A % B

4. 증감연산자

- ++ (1씩 증가)
  -- (1씩 감소)
- 증가연산자(++) => 숫자형 데이터를 1씩 증가
  (변수++; 또는 ++변수;)
- 감소연산자(--) - 숫자형 데이터를 1씩 감소
  (변수--; 또는 --변수;)

  (중요)
  var a = ++b; b를 1 증가 시킨 후 a에 대입
  var a = b++; a에 대입 후 b를 1 증가
  ++가 뒤에 있으면 대입부터, ++가 앞에 있으면 연산부터 한다.

  var num2 = num++; // (1) 대입=, (2) ++
  var num2 = ++num; // (1) ++, (2) 대입

5. 비교연산자

- 두 데이터를 '크다', '작다', '같다'와 같이 비교할때 사용
- 크다(>), 작다(<), 크거나 같다(>=), 작거나 같다(<=)
  - 같다(==), 같지 않다(!=, !==)
- 연산의 결과가 논리값(blooean : 참(true), 거짓(false)) -> 판별식에서 주로 사용 (조건식, 반복문)

  (예시)
  A == B A와 B는 같다 데이터 일치 여부만 체크( 10 == "10" -> true)
  A != B A와 B는 다르다 데이터 불일치 여부만 체크( 10 != "10" -> false)
  A === B A와 B는 같다 데이터 일치 + 데이터 종류 일치 여부 체크(10 === "10" --> false)
  A !== B A와 B는 다르다 데이터 불일치 + 데이터 종류 불일치 여부 체크(10 !== "10" --> true)

  (참고)
  동일성 비교 : 동일한 주소(===)
  동등성 비교 : 동등한 가치(==)

  (참고)
  ! => 부정 연산(NOT): 참 -> 거짓, 거짓 -> 참

6. 논리연산자

- AND 연산 : 교집합과 비슷. 전부 true 일때 true(&&)
- OR 연산 : 합집합과 비슷. 어느 하나라도 true 일때 true (||)
- || OR 연산자, 비교하는 대상 중 하나라도 true면 true가 됨
- && AND 연산자, 비교하는 대상 모두 true일때 true, 그렇지 않다면 false
- 부정 연산(NOT) 피 연산자의 값을 반대로 바꿈, true -> false, false -> true
- ! : true -> false / false -> true

- 논리 연산의 값 : 최종 연산의 값
- OR (||) : 기본값. 어떤 조건이든 참이면 참 num = num || 10;
- AND (&&) : 간단한 조건식을 대체. 하나라도 거짓이면 거짓

7. 부호연산자
   - ( + - ) 부호를 반전시키는 연산자
   - : 부호 반전 (음수 -> 양수, 양수 ->음수)
   - (\* - 1)

# 연산자 우선순위

- 위에서 부터 우선 순위가 높음
  ()
  단항 연산자(--, ++, !)
  산술 연산자(_, /, %, +, -)
  비교 연산자(>, >=, <, <=, ==, ===, !=, !==)
  논리 연산자(&&, ||)
  대입(복합 대입)연산자(=, +=, -=, _=, /=, %=)

      (예시)
        ++A * B <= C
         1번 순서 - 단항 연산자 ++A
         2번 순서 - * B
         3번 순서 - C와 비교(<=)

      (예시)
        var num = 10;
        ++num > 10  (++가 먼저 적용)
        true

        var num = 10;
        num++ > 10  (>가 먼저 적용)
        false

  (참고)

  - false로 인식하는 값
    : 0, '(비어있는 값)', undefined, null

  - true로 인식하는 값
    : false로 인식하는 값 이외의 값, 문자열'0'은 참, ''속에 공백 넣으면 참

  - 논리 연산의 값 : 최종 연산의 값

# ★★★(중요 참고) 단락 회로 평가

    - 비교연산과 논리연산은 값이 나오는 것이 목적이 아니라 비교하는것이 목적
    - 참과 거짓을 판별하는 것이 주 목적
    - 자바스크립트 연산에서 연산의 목적이 끝나면 그 시점의 값이 나옴
    - 연산이 중간에 끝나면 그 시점의 값이 나오고, 끝까지 진행되면 마지막 값이 나옴

        var num1 = 0;
        var num2 = 10;
        var num3 = num1 && num2;
        num3: 0
        (0은 false 이므로 연산이 끝나서 이 시점의 값인 num1의 0이 나온다)

        var num1 = 0;
        var num2 = 10;
        var num3 = num1 || num2;
        num3: 10
        (0이 fals여도 ||는 연산이 끝까지 가기 때문에 마지막까지 계산 후 마지막 값인 num2의 10이 나온다)

# 삼항 조건 연산자

- 조건식 ? 참일때 : 거짓일때
  (1항) (2항) (3항)

- (참고)
  조건식 : 참 거짓을 판별하는 판별식 (주로 비교, 논리 연산...)
  식 : 연산식
