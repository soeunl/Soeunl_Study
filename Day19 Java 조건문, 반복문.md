<Day19 - 0415>
<JAVA 조건문, 반복문>

# 조건문

- 조건문이란? : 주어진 조건에 따라 다른 문장을 선택할 수 있도록 프로그래밍 하는 것

---

# if문과 if-else문

- 조건문의 가장 단순한 형식
- 주어진 조건식이 '참'일 경우에 중괄호 안에 있는 문장을 수행
- 조건식에는 결과가 참, 거짓으로 판별되는 식이나, 참, 거짓의 값을 가진 변수, 상수를 사용할 수 있음
- 연산의 결과가 참, 거짓이 되는 관계 연산자를 자주 사용함
- 조건식을 만족하는 경우와 만족하지 않는 경우를 모두 나나탤 때는 if-else문을 사용함
- else문은 조건식을 사용하지 않음
- if-else문은 조건 연산자로도 구현할 수 있음
- 간단한 조건문이고 선택이 두가지만 있는 경우 종종 조건 연산자도 사용

```Java

if-else문

    if (a > b)
        max = a;
    else
        max = b;

조건 연산자 (삼항조건)

    max = (a > b)? a : b;

```

---

# switch-case문

- 조건식의 결과가 정수 또는 문자열 값이고 그 값에 따라 수행되는 경우가 각각 다른 경우에는 switch-case 문으로 구현
- case문에는 여러 문장이 있어도 {}를 여러 번 사용하지 않고 한번만 사용
- 키워드는 정수, int, char만 사용
- ENUM 상수, 문자열 상수도 사용할 수 있음 (따지고 보면 정수)

```Java

switch(조건) {
	case 값1: 수행문1;
		break;
	case 값2: 수행문2;
		break;
	case 값3: 수행문3;
		break;
	default: 수행문4;
}

```

- break문은 switch-case문의 수행을 멈추고 빠져나가도록 함
- break를 쓰지 않으면 다음 break를 만날때까지 다음 case 부분이 실행됨
- JDK1.7부터는 switch-case문의 case값에 정수 값 뿐 아니라 문자열도 사용할 수 있음
- default : 해당되는 값이 없을 때

---

# 반복문

## while문

    - while문은 조건을 먼저 검사하기 때문에 조건식이 맞기 않으면 반복 수행이 한 번도 일어나지 않음

```Java

while(조건식) {
	수행문1;  // 조건식이 참인 동안 반복 수행
}

```

---

## while문이 무한히 반복되는 경우

```Java

while(true) {
	...
}

```

---

## do-while문

    - do-while문은 {}안의 문장을 무조건 한 번 수행한 후에 조건식을 검사함. 즉, 조건이 만족하는지 여부를 마지막에 검사함
    - 중괄호 안의 문장을 반드시 한 번 이상 수행해야 할 때 while문 대신 do-while문을 사용함

```Java

do {
	수행문1;
	...
} while(조건식);

```

---

## for 문

    - 반복문 중에서 가장 많이 사용하는 반복문
    - for문은 반복문을 구현하는데 필요한 여러 요소(변수의 초기화식, 조건식, 증감식)를 함께 작성하여야 함

```Java

for(초기화식; 조건식; 증감식) {
	수행문;
}

// 초기화식 : for문이 시작할 때 딱 한번만 수행하며 사용할 변수를 초기화함
// 조건식 : 언제까지 반복수행할 것인지 구현함
// 증감식 : 반복 횟수나 for문에서 사용하는 변수 값을 늘리거나 줄임
// 반복 중단 : break
// 반복 건너뛰기 : continue (현재 반복을 중단, 새로 시작)

```

---

## for문을 자주 사용하는 이유

    - for문을 사용하여 구현하면 초기화, 조건비교, 증감식을 한 줄에 쓸 수 있고 가독성도 좋아짐
    - for문은 배열과 함께 자주 사용함. 배열은 자료형이 순서대로 모여있는 구조인데, 배열 순서를 나타내느 색인은 항상 0부터 시작함. 따라서 배열의 전체 요소 개수가 n개일 때, 요소 위치는 n-1번째로 표현할 수 있음
    - 이러한 배열의 특성과 증감에 따른 반복을 표현하는 데 적합한 for문의 특성 때문에 for문과 배열을 함께 자주 사용하는 것임

---

## for문 요소 생략하기

```Java

1. 초기화식 생략
int = 0;
for ( ; i < 5; i++) {
	...
}

2. 조건식 생략
for(i = 0;  ; i++) {
	sum += i;
	if (sum > 200) break;
}

3. 증감식 생략
for(i = 0; i < 5;  ) {
	...
	i = (++i) % 10;
}

4. 요소 모두 생략
모든 요소를 생략하고 무한 반복하는 경우에 사용
for ( ; ; ) { ... }

```

---

## 중첩된 반복문

```Java

public class NestedLoop {
	public static void main(String[] args) {
		int dan;
		int times;

		for (dan = 2; dan <= 9; dan++) {
            // 2단부터 9단까지 반복하는 외부 반복문
			for (times = 1; times <= 9; times++) {
                // 각 단에서 1~9를 곱하는 내부 반복문
				System.out.println(dan + "X" + times + " = " + dan * times);
                // System.out.printf("%d X %d = %d%n", dan, times, dan * times);
			}
			System.out.println();
		}
	}
}

```

- 반복문 안에 반복문

System.out.println(값); : 출력 + 줄개행(\n)
print(값) : 출력 (줄개행 X)
println() : 줄개행(\n)
printf(형식화)
%s -> 문자열 대체
%d -> 정수 대체 / decimal
%f -> 실수 대체 /float
%n -> 줄개행 / \n
