Day 01 - ABAP 기본 문법 및 제어문

학습 목표
ABAP의 기본적인 문법을 이해하고 변수, 자료형, 출력, 연산자, 조건문, 반복문을 활용하여 간단한 프로그램을 작성

변수와 자료형
변수 선언
ABAP에서는 DATA를 사용하여 변수를 선언

DATA name TYPE string.
DATA age TYPE i.


1. 주요 자료형
string : 문자열
i : 정수


2. 값 대입
=를 사용해 변수에 값을 대입
name = 'Apple'.
age = 20.


3. 데이터 출력
WRITE를 사용하여 데이터를 출력
WRITE: / '이름:', name.
WRITE: / '나이:', age.
/를 사용시 줄을 바꿔서 출력


4. IF 조건문
조건에 따라 다른 코드를 실행 가능
IF age >= 20.
    WRITE: '성인입니다.'.
ELSE.
    WRITE: '미성년자입니다.'.
ENDIF.

조건문은 다음과 같은 구조로 사용

IF
ELSEIF
ELSE
ENDIF

ENDIF를 사용해 IF 조건문의 끝을 의미


5.ELSEIF를 이용한 여러 조건
조건이 여러 개인 경우 ELSEIF를 여러 번 사용 가능

DATA score TYPE i.

score = 85.

IF score >= 90.
    WRITE: 'A'.
ELSEIF score >= 80.
    WRITE: 'B'.
ELSEIF score >= 70.
    WRITE: 'C'.
ELSE.
    WRITE: 'F'.
ENDIF.

score = 85이므로 결과는 B

조건은 위에서부터 순서대로 확인, 처음으로 참이 되는 조건의 코드가 실행


6.계산 결과를 조건문에 활용
상품 가격과 수량을 이용하여 총 금액을 계산, 총 금액에 따라 조건을 판단하는 프로그램을 작성

DATA price TYPE i.
DATA quantity TYPE i.
DATA total TYPE i.

price = 15000.
quantity = 3.

total = price * quantity.

WRITE: / '총 금액:', total.

IF total >= 50000.
    WRITE: / '10% 할인 대상입니다.'.
ELSE.
    WRITE: / '할인 대상이 아닙니다.'.
ENDIF.


7.DO 반복문
DO ... TIMES를 사용하면 정해진 횟수만큼 코드를 반복

DATA num TYPE i.

num = 1.

DO 5 TIMES.
    WRITE: / num.
    num = num + 1.
ENDDO.

결과:
1
2
3
4
5

구조
DO 반복횟수 TIMES.
    반복할 코드
ENDDO.

ENDDO는 DO 반복문의 종료를 의미


8.MOD 연산자
MOD는 나눗셈의 나머지를 구할 때 사용

IF num MOD 2 = 0.

위 조건은 num을 2로 나눈 나머지가 0인지 확인
따라서 짝수인지 판단할 때 사용 가능

2 MOD 2 = 0
3 MOD 2 = 1
4 MOD 2 = 0


9.DO + IF + MOD
반복문과 조건문을 함께 사용해 1~10의 숫자 중 짝수만 출력하는 프로그램을 작성

DATA num TYPE i.

num = 1.

DO 10 TIMES.
    IF num MOD 2 = 0.
        WRITE: / num.
    ENDIF.

    num = num + 1.
ENDDO.

결과:
2
4
6
8
10


10.WHILE 반복문
WHILE은 조건이 참인 동안 코드를 반복

DATA num TYPE i.

num = 1.

WHILE num <= 5.
    WRITE: / num.
    num = num + 1.
ENDWHILE.

결과:
1
2
3
4
5

DO와 WHILE의 차이
DO ... TIMES : 정해진 횟수만큼 반복
WHILE : 조건이 참인 동안 반복


11.WHILE + IF + MOD

WHILE 반복문과 IF 조건문, MOD 연산자를 함께 사용해 1~ 10의 숫자 중 짝수만 출력

DATA num TYPE i.

num = 1.

WHILE num <= 10.
    IF num MOD 2 = 0.
        WRITE: / num.
    ENDIF.

    num = num + 1.
ENDWHILE.

결과:
2
4
6
8
10


12. Mini Project - 쇼핑몰 할인 계산
오늘 배운 변수, 연산자, 출력, 조건문을 활용해 간단한 할인 계산 프로그램 만들어 보기

조건
상품 가격: 18,000원
수량: 4개
70,000원 이상 -> 15% 할인
50,000원 이상 -> 10% 할인
30,000원 이상 -> 5% 할인
30,000원 미만 -> 할인 없음

코드
DATA price TYPE i.
DATA quantity TYPE i.
DATA total TYPE i.

price = 18000.
quantity = 4.
total = price * quantity.

WRITE: / '총 금액:', total.

IF total >= 70000.
    WRITE: / '15% 할인 대상입니다.'.
ELSEIF total >= 50000.
    WRITE: / '10% 할인 대상입니다.'.
ELSEIF total >= 30000.
    WRITE: / '5% 할인 대상입니다.'.
ELSE.
    WRITE: / '할인 대상이 아닙니다.'.
ENDIF.

결과:
총 금액: 72000
15% 할인 대상입니다.


13. 오늘 배운 핵심
변수
DATA 변수명 TYPE 자료형.

값 대입
변수 = 값.

출력
WRITE: 값.

조건문
IF 조건.
    실행할 코드
ELSEIF 조건.
    실행할 코드
ELSE.
    실행할 코드
ENDIF.

반복문
DO 5 TIMES.
    실행할 코드
ENDDO.

WHILE 조건.
    실행할 코드
ENDWHILE.

문장 종료
ABAP에서는 대부분의 명령문 끝에 .을 사용


14. 오늘 공부하면서 알게 된 점
- ABAP에서 변수는 DATA를 사용하여 선언
- 변수 선언 시 자료형을 지정
- WRITE를 이용하여 데이터를 출력
- IF, ELSEIF, ELSE를 이용하여 조건에 따라 다른 코드를 실행
- ELSEIF는 여러 번 사용가능
- DO ... TIMES는 정해진 횟수만큼 반복할 때 사용
- WHILE은 조건이 참인 동안 반복
- MOD를 이용하여 나머지를 구할 수 있고 짝수/홀수 판별에 활용 가능
- 반복문 안에 조건문을 넣어 조건에 따라 특정 작업만 수행 가능


15. 오늘의 실습
오늘 직접 작성한 프로그램
- 변수와 자료형을 이용한 데이터 저장
- 나이에 따른 성인/미성년자 판별
- 점수에 따른 A/B/C/F 등급 판별
- 상품 가격과 수량을 이용한 총 금액 계산
- 총 금액에 따른 할인율 판별
- DO 반복문을 이용한 숫자 출력
- MOD를 이용한 짝수 판별
- WHILE 반복문을 이용한 숫자 출력
- 조건문과 반복문을 결합한 프로그램 작성
- 쇼핑몰 할인 계산 미니 프로젝트
