<Day38- 0513>
<Database 입출력, java.io 패키지>

## 입출력(I/O) java.io 패키지

1. 입출력이란?

   - Input/Output 입력 / 출력
   - 입력과 출력을 말함
   - 컴퓨터 내부 또는 외부와 프로그램간의 데이터를 주고받는 것

2. 스트림(stream)
   - 데이터가 이동하는 통로
   - 입력 통로(입력 스트림)
   - 출력 통로(출력 스트림)
   - 데이터를 운반하는데 사용되는 연결통로
   - 스트림은 단방향 통신만 가능하기 때문에 하나의 스트림으로 입력과 출력을 동시에 처리할수는 없음

❤️ 바이트기반 스트림(1바이트) : 데이터 크기가 바이트 단위 / 1바이트씩 읽어오는 스트림

1.  💙 입력 스트림 - InputStream : 추상 클래스
    InputStream : int read()

    💛 기반 스트림 : 직접 데이터에 접근해서 읽어오는 스트림
    FileInputStream
    ByteArrayInputStream

    (참고)
    Unsigned : 양의 정수
    Unsined Byte 0~255

    입력 스트림의 끝에 도달한 경우 반환값이 -1 / 바이트 범위에서 부족 -> 더 큰 자료형
    int read()

    💛 보조 스트림
    : 다른 스트림에 추가적인 기능을 부여
    : 데이터를 입출력 할 수 있는 기능은 없음
    : 기반 스트림의 기능을 향상시키거나 새로운 기능을 추가할 수 있음
    : 보조스트림만으로는 입출력을 처리할 수 없고, 스트림을 먼저 생성한 다음에 이를 이용해서 보조스트림을 생성해야 함

    - 생성자 매개변수 InputStream
      FilterInputStream : 보조스트림의 체계를 정리하기 위한 클래스 (BufferedInputStream, DataInputStream- 기본형으로 데이터를 읽어올 수 있는 추가기능)
      ObjectInputStream
      InputStreamReader

      - 한가지 자료형으로 사용하는 것이 편함

2.  💙 출력 스트림 - OutputStream : 추상 클래스

        💛 기반 스트림 : 직접 데이터에 접근해서 출력하는 스트림
        FileOutputStream
        ByteArrayOutputStream

        💛 보조 스트림 : 다른 스트림에 추가적인 기능을 제공

        - 생성자 매개변수 OutStream
          FilterOutputStream : 보조스트림의 체계를 정의하기 위한 클래스 (BufferedOutputStream, DataOutptStream)
          ObjectOutputStream
          OutputStreamWriter

          - 한가지 자료형으로 사용하는 것이 편함

        (참고)
        데코레이터 패턴
        (핵심 기능을 추가기능(목적)과 함께 대신해서 수행해주는 패턴)
        핵심 기능이 목적이 아님

        class BufferedInputStream extends InputStream {

        private InputStream in;

        public BufferedInputStream(InputStream in) {

        this.in = in;

        }

        // read 메서드의 기능은 추가적인 기능과 함께 다른 스트림의 기능을 대신 수행

        public int read() {

            // 버퍼 기능에 대한 코드... // 추가 기능

            int byte = in.read();

            // 버퍼 기능에 대한 코드... //추가 기능

            return byte;

        }

    }

❤️ 문자기반 스트림 : 데이터 크기가 문자 단위(유니코드 - 2, 3 바이트)

1. 💙 입력 스트림 - Reader : 추상 클래스
   기반 스트림
   보조 스트림

2. 💙 출력 스트림

🤍 표준입출력 : 콘솔에 입력, 출력

1. System.in : InputStream / 터미널에서 입력, 바이트 단위 스트림, 문자 단위 스트림으로 변경(InputStreamReader)
2. System.out : PrintStream : 문자 단위 출력 스트림, print(...), printf(...), println(...) + 버퍼(8kb)
3. System.err : PrintStream : 표준 에러스트림, 글자 색이 빨간색

PrintStream : 문자 기반 스트림, 기반 스트림, 버퍼

- print(), printf(), println() 편의 메서드 포함
  (참고) PrintWriter : 문자 단위 출력 스트림 + 버퍼(8kb) print(), printf(), println()

❤️ File

- 파일, 디렉토리를 파일 객체로 생성해서 관리
- 파일, 디렉토리에 유용한 기능...

  윈도우즈 : D:￦경로명￦파일명.확장자 -> ￦
  (참고) D:/경로명/파일명.확장자

  리눅스(맥) : /home/project/파일명 -> /

  환경 변수(OS내에서 사용가능한 변수) 구분문자
  윈도우즈 : ; (세미콜론)
  리눅스(맥) : :(콜론)
  -> File.pathSeperator

  쓰기, 읽기, 실행 권한
  boolean canRead() : 읽기 권한 여부
  boolean canWrite() : 쓰기 권한 - false이면 수정, 삭제 X
  boolean canExecuse() : 실행 권한

  void setReadable(..)
  void setWritable(..)
  void setExecutavble(..)

  void setReadOnly() : 읽기 전용

  String getAbsolutePath() : 파일 전체 경로
  String getCanonial

  String getName() : 파일명
  String getPath() : 파일 경로

🤍 직렬화(Serialization)

- 객체를 데이터 스트림으로 만는 것
- 객체에 저장된 데이터를 스트림에 쓰기(write)위해 연속적인(serial) 데이터로 변환하는 것
- 자바객체를 전송할 수 있는 형태인 텍스트로 바꿈
- 객체마다 다른 값을 바꾼다. 그 바꾸는 것이 바로 인스턴스변수

- 직렬화 -> 데이터노출 -> 위험한 작업 -> 의사 표현(Serialable 인터페이스 추가 -> 진행하겠음을 표현)
- Serialization 인터페이스 (구현 내용 X - 마커 인터페이스)
- Serialization 인터페이스로 데이터 노출이 있더라도 할거라고 알려주어야 함
  -> 변환 값 : 다시 객체로 복구할 때 필요한 항목 직렬화
  -> 객체마다 변경될 수 있는 값(인스턴스 변수)

(참고) 스트림으로부터 데이터를 읽어서 객체를 만드는 것을 역직렬화(deserialization)라고 함

1. ObjectInputStream : 객체 형태로 읽어 오는 것
   -> 객체로 복구(새로 생성 <- 객체마다 다른 데이터(인스턴스 변수 값)를 주입), 역직렬화(스트림으로 부터 객체를 입력)
   -> 역직렬화는 직렬화할 때와는 달리 입력스트림을 사용하고 readObject()를 사용하여 저장된 데이터를 읽기만 하면 객체로 역직렬화 됨
   -> 다만 readObject()의 반환타입이 Object이기 때문에 객체 원래의 타입으로 형변환 해주어야 함

2. ObjectOutputStream : 객체 형태로 저장
   -> 객체 형태로 저장
   -> 객체를 복구할 때 필요한 항목 저장
   (복구가 필요한 데이터? 객체마다 다른)
   -> ObjectOuputStream의 writeObject(Object obj)를 사용해서 객체를 출력하면, 객체가 파일에 직렬화되어 저장됨

🤍 직렬화가 가능한 클래스 만들기 - Serializable, transient

- 직렬화가 가능한 클래스를 만드는 방법은 클래스가 java.io.Serializable인터페이스를 구현하도록 하면 됨
- Serializable 인터페이스는 아무런 내용도 없는 빈 인터페이이지만, 직렬화를 고려하여 작성한 클래스인지를 판단하는 기준이 됨 (Serializable을 구현한 클래스를 상속받는다면 Serializable을 구현하지 않아도 됨 / 하지만 상위클래스가 Serializable을 구현하지 않았다면 하위클래스를 직렬화할 때 상위클래스에 정의된 인스턴스 변수는 직렬화 대상에서 제외됨★★★)
- 모든 클래스의 가장상위 클래스인 Object는 Serializable을 구현하지 않았기 때문에 직렬화할 수 없음
- 제어자 transient를 붙여서 직렬화 대상에서 제외되도록 할 수 있음
- transient가 붙은 인스턴스 변수의 값은 그 타입의 기본값으로 직렬화된다고 볼 수 있음

(참고) static변수나 상수는 직렬화 X

AOP
// 옵져버 패턴
