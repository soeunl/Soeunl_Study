<Day24 - 0422>
<JAVA 내부클래스>

# 내부 클래스

- 클래스 안에 클래스가 정의된 형식
- 클래스 내부에 선언한 클래스

1. 인스턴스 내부 클래스

- 멤버 변수, 멤버 메서드와 비슷한 성격
- 외부 클래스의 객체 생성 이후 접근 가능한 클래스 (인스턴스 내부 클래스는 외부 클래스 생성 후 생성되기 때문)
- 외부 클래스의 변수도 같은 인스턴스 자원으로 내부클래스에서 접근이 가능함

❤️ 인스턴스 내부 클래스는 언제 사용하나?

- 외부 클래스 내부에서만 생성하여 사용하는 객체를 선언할 때 사용함
- Outer.this를 통해 내부 클래스에서 외부 클래스 자원에 접근가능
- 외부 클래스 객체가 생성되어야 내부 클래스 객체가 생성되는 구조이므로 내부 클래스에는 static을 정의할 수 없으나, 버전 업데이트가 되면서 가능해짐

2. 정적 내부 클래스

- 정적 내부 클래스는 인스턴스 내부 클래스처럼 외부 클래스의 멤버 변수와 같은 위치에 정의하며 static 예약어를 함께 사용
- 정적 내부 클래스에서 외부 클래스의 인스턴스 변수는 사용할 수 없음

❤️ 정적 내부 클래스는 언제 사용하나?

- 내부 클래스가 외부 클래스 생성과 무관하게 사용할 수 있어야 하고, 정적 변수도 사용할 수 있어야 한다면 정적 내부 클래스를 사용하면 됨
- 내부 클래스를 만들고 외부 클래스와 무관하게 다른 클래스에서도 사용하려면 정적 내부 클래스를 생성하면 됨
- 하지만 정적 내부 클래스를 private으로 선언했다면 이것 역시 다른 클래스에서 사용할 수 없음

3. 지역 내부 클래스

- 함수 안에 정의된 클래스 (메서드 내부에 클래스를 정의하여 사용하는 것)
- 이 클래스는 메서드 안에서만 사용할 수 있음

❤️★★★ 지역 내부 클래스에서 사용하는 지역 변수

- 지역 내부 클래스에서 사용하는 메서드의 지역 변수는 상수로 처리됨(데이터영역에 저장되어 제거되지 않고 사용하기 위해 지역변수를 상수화하여 유지함)
- 상수로 처리하기 위해 JDK1.7까지는 al 예약어를 꼭 함께 써야 했으나, JDK1.8 부터는 직접 써 주지 않아도 코드를 컴파일 하면 final 예약어가 자동으로 추가됨

❤️ 인터페이스, 추상 클래스가 객체가 되는 조건
① 환경 : 지역 내부, 클래스의 멤버 변수에서 객체 생성
② 미구현된 메서드의 재정의를 통해서 완전한 객체 생성 (미구현된 메서드 구현)

- 함수형 프로그래밍 : 매개변수, 반환값
- 람다식, 스트림

(참고)

- 자료형의 종류

1. 기본자료형
2. 참조자료형
