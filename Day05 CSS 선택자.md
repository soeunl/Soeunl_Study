<Day05 - 0325>
<CSS 선택자>

# CSS 선택자
    1. 전체 선택자
         - 모든 요소에 스타일 적용하기
         - 전체 선택자로 *(별표)를 사용
         - 문서의 여백이나 글꼴 크기 등 기본 스타일을 초기화할 때 사용
         - * { 속성: 속성값; 속성: 속성값; ... }

    2. 태그 선택자
        - 태그명으로 요소를 선택
        - p {
                font-size: 12px;  /* 글자 크기 */
                font-family: 돋움; /* 글꼴 */
            }

    3. 클래스(class) 선택자
        - 동일한 형태의 여러곳에 스타일 적용
        - 복수개 선택시
        - 클래스 선택자는 태그 대신 클래스 이름을 사용
        - 클래스 이름 앞에는 반드시 마침표(.)를 붙여야 함
        - .클래스명 { 스타일 }
        - 클래스는 띄어쓰기를 통해서 여러개의 클래스를 적용할 수 있음

    4. id 선택자
        - 단일한 한 곳에 스타일 적용
        - 단수개 선택
        - 웹 문서 안의 특정 부분에 스타일을 지정할 때 사용
        - #기호를 사용함
        - #아이디명 { 스타일 }
        - 클래스 선택자가 문서 안에서 여러 번 적용할 수 있는 스타일인 반면, id 선택자는 문서 안에서 한 번만 적용할 수 있음
        - 우선순위가 class 선택자보다 높음

    * 스타일 적용 우선순위
        1. 범위가 넓을수록 우선순위는 낮음
        2. 범위가 좁을수록 우선순위가 높음
            (태그선택자 < 클래스 선택자 < 아이디 선택자 < style 속성에 적용 < !important 적용)

    * !important : 우선 순위 강제 적용

    * 같은 클래스, 태그 -> 나중에 적용된 선택자가 우선 순위가 높음. 가장 아래 적용된 선택자가 우선순위 높음. 위에서부터 순차적으로 내려오며 적용되기 때문

    5. 그룹 선택자
        - 둘 이상 요소에 같은 스타일 적용
        - 여러 선택자에 같은 스타일이 사용되는 경우 쉼표(,)로 구분해 여러 선택자를 나열한 후 스타일은 한번만 정의할 수 있음
        - ,로 그룹 지어서 선택
        - h1, h2 {
                    text-align: center; /* 가운데 정렬 */
                }

    6. 조상 자손 선택자
        - 조상 선택자 ... 자손 선택자 {

        } 
        - 위로 갈수록 조상, 아래쪽으로 갈수록 자손을 배치
        - body ul li {
        }

    7. 속성명, 속성명 = 값으로도 선택
        - 선택자[속성명]
            input[type] : input 태그에 type 속성이 있는 모든 요소
        - 선택자[속성명="값"]
            input[type="text"] : input 태그에 type 속성 값이 text인 요소
        - 선택자[속성명 ^= "키워드"]
            input[type^="te"] : input 태그에 type 속성 값이 te 키워드로 시작하는 요소
        - 선택자[속성명 ~= "키워드"]
            input[type~="ex"] : input 태그에 type 속성 값이 ex 키워드가 포함된 요소
        - 선택자[속성명 $= "키워드"]
            input[type$="xt"] : input 태그에 type 속성 값이 xt로 끝나는 요소

    * 결합자
        - 1. 부모 자식 선택자
            -  ● 부모 : 바로 위 요소
            -  ● 자식 : 바로 아래 요소
                    부모선택자 > 자식선택자 {}

        - 2. 형제 선택자 
            -  ● 형제 선택자 : 선택자 기준 오른쪽 형제요소
                    선택자 + 인접 형제 선택자 {}
            -  ● 인접 형제 선택자 : 바로 오른쪽 옆 형제 요소
                    선택자 + 인접형제선택자 {}

        - 3. 가상 클래스 선택자
            -  요소의 상태
                ● 선택자 : 상태속성
                => :checked (체크된 상태 선택)
                => :selected (선택된 상태 선택)
                => :hover (마우스를 올린 상태 선택)
                => :focus (입력 대기 상태 선택)
                
                (예시)
                input[type="checkbox"]:checked + label {
                background: gray;
                }

                input[type="text"]:focus{
                background: yellow;   
                }

            - 요소의 순서
                ● first-child : 첫번째 자식 요소 선택 / :first-of-type
                ● last-child : 마지막 자식 요소 선택 / :last-of-type
                ● nth-child() / nth-of-type
                        : nth-child(숫자) => 숫자 번째 자식 요소 선택 (1부터 시작) 
                        : nth-child(수식) => 수식에 해당하는 요소를 선택 (2n = 짝수, 2n+1 = 홀수)

            - 조건에 따라서 선택
                ● :not(선택자) : 선택자를 제외한 모든 요소

            - 가상의 요소를 추가, 선택
                ● (::)
                    - ::before : 자식 요소의 첫번째에 가상의 요소 추가, 선택
                    - ::after : 자식 요소의 마지막에 가상의 요소를 추가, 선택

                    ★ 필수 속성 : content: '내용...'
                        content 속성이 꼭 있어야 함


    * 참고
        - transition : 전환효과 -> 애니메이션 효과