---
layout: post
title: JAVA_sparta - wekk01
date: 2024-04-23
category: JAVA_sparta
---


## Operator.java
```java
package week2;

public class Operator {
    public static void main(String[] args) {
// 연산자, 피연산자
        int x = 5;
        int y = 10;
        int z = x + y;  // 5(피연산자) +(연산자) 10(피연산자) 계산
        System.out.println(z);  // 출력값 : 15

// 사칙 연산 : + - * / %
        System.out.println(4 + 2); // 6
        System.out.println(4 - 2); // 2
        System.out.println(4 * 2); // 8
        System.out.println(4 / 2); // 2
        System.out.println(5 / 2); // 2
        System.out.println(2 / 4); // 0
        System.out.println(4 % 2); // 0
        System.out.println(5 % 2); // 1

        // 우선 순위 연산
        System.out.println(2 + 2 * 2); // 6
        System.out.println((2 + 2) * 2); // 8
        System.out.println(2 + (2 * 2)); // 6

        // 변수를 이용한 연산
        int a = 20;
        int b = 10;
        int c;

        // 덧셈
        c = a + b;
        System.out.println(c); // 30

        // 뺄셈
        c = a - b;
        System.out.println(c); // 10

        // 곱셈
        c = a * b;
        System.out.println(c); // 200

        // 나눗셈 (몫)
        c = a / b;
        System.out.println(c); // 2

        // 나눗셈 (나머지) = 나머지 연산
        c = a % b;
        System.out.println(c); // 0

// 비교 연산자 (참이면 true, 거짓이면 false) :  > < >= <= == !=
        System.out.println(10 > 9); // 10 는 9 보다 크다 (참이면 true, 거짓이면 false)
        System.out.println(10 >= 9); // 10 는 9 보다 크거나 같다 (true)
        System.out.println(10 < 9); // 10 는 9 보다 작다 (false)
        System.out.println(10 <= 9); // 10 는 9 보다 작거나 같다 (false)
        System.out.println(10 == 10); // 10 는 10 와 같다 (true)
        System.out.println(10 == 9); // 10 는 9 과 같다 (false)
        System.out.println(10 != 10); // 10 는 10 와 같지 않다 (false)
        System.out.println(10 != 9); // 10 는 9 과 같지 않다 (true)

// 논리 연산자 && || !
        boolean flag1 = true;
        boolean flag2 = true;
        boolean flag3 = false;

        System.out.println(flag1); // true
        System.out.println(flag2); // true
        System.out.println(flag3); // false

        // 피연산자 중 하나라도 true 이면 true
        System.out.println(flag1 || flag2); // true
        System.out.println(flag1 || flag2 || flag3); // true
        // 피연산자 모두 true 이면 true
        System.out.println(flag1 && flag2); // true (flag1, flag2 모두 true 라서)
        System.out.println(flag1 && flag2 && flag3); // false (flag3은 false 라서)

        // And 연산
        System.out.println((5 > 3) && (3 > 1)); // 5 는 3 보다 크고, 3 은 1 보다 크다 (true)
        System.out.println((5 > 3) && (3 < 1)); // 5 는 3 보다 크고, 3 은 1 보다 작다 (false)

        // Or 연산
        System.out.println((5 > 3) || (3 > 1)); // 5 는 3 보다 크거나, 3 은 1 보다 크다 (true)
        System.out.println((5 > 3) || (3 < 1)); // 5 는 3 보다 크거나, 3 은 1 보다 작다 (true)
        System.out.println((5 < 3) || (3 < 1)); // 5 는 3 보다 작거나, 3 은 1 보다 작다 (false)

        // 비교연산은 한 번에 두 개만 가능함.
        // 1<3 && 3<5 로 써야 함.
        // System.out.println(1 < 3 < 5); // 불가능한 코드

        // 논리 부정 연산자
        System.out.println(!flag1); // false (flag1 값의 반대)
        System.out.println(!flag3); // true (flag3 값의 반대)
        System.out.println(!(5 == 5)); // false
        System.out.println(!(5 == 3)); // true

// 대입 연산자 += -= *= /= =
        int number = 10;
        number = number + 2;
        System.out.println(number); // 12

        number = number - 2;
        System.out.println(number); // 10

        number = number * 2;
        System.out.println(number); // 20

        number = number / 2;
        System.out.println(number); // 10

        number = number % 2;
        System.out.println(number); // 0

        number = number++;
        System.out.println(number); // 2

        number = number--;
        System.out.println(number); // 0

// 복합 대입 연산자
        number = 10;

        number += 2;
        System.out.println(number); // 12

        number -= 2;
        System.out.println(number); // 10

        number *= 2;
        System.out.println(number); // 20

        number /= 2;
        System.out.println(number); // 10

        number %= 2;
        System.out.println(number); // 0

// 대입 증감 연산자
        int e = 10;
        int f = 10;
        int val = ++e + f--; // a 는 연산전에 +1, b 는 연산후에 -1

        System.out.println(e); // 11
        System.out.println(f); // 9
        System.out.println(val); // 21
        // 11 + 9 가 왜 21이 나오는 이유
        // e는 1 더하고 연산. f는 연산 후 1 빼기
        // 따라서 val = 11 + 10 = 21

        int g = e--; // g 에 e 값 대입 후 e-1  (즉, e=10, g=11)
        int h = ++f; // f 값 +1 후에 h 에 대입 (즉, f=10, h=10)
        int val1 = g-- * ++h; // g 는 연산후에 -1, h 는 연산전에 +1

        System.out.println(e); // 10
        System.out.println(f); // 10
        System.out.println(g); // 11
        System.out.println(h); // 10
        System.out.println(val1); // 11 * 11 = 121
        // g는 11로 계산 후 1 뺴기. h는 1 더해서 11로 계산.
        // 따라서 val1 = 11*11 = 121

// 형변환 연산자
        int intNumber = 93 + (int) 98.8; // 93 + 98
        double doubleNumber = (double) 93 + 98.8; // 93.0 + 98.8

// 삼항 연산자
        int xx = 1;
        int yy = 9;

        boolean i = (xx == yy) ? true : false;
        System.out.println(i); // false

        String s = (xx != yy) ? "정답" : "땡";
        System.out.println(s); // 땡

        int max = (xx > yy) ? xx : yy;
        System.out.println(max); // 9

        int min = (xx < yy) ? xx : yy;
        System.out.println(min); // 1

// 연산자 우선순위
        x = 2;
        y = 9;
        z = 10;

        boolean result = x < y && y < z; // <,> 비교연산자 계산 후 && 논리 연산자 계산
        System.out.println(result); // true

        result = x + 10 < y && y < z; // +10 산술연산자 계산 후 <,> 비교연산자 계산 후 && 논리 연산자 계산
        System.out.println(result); // false

        result = x + 2 * 3 > y; // 산술연산자 곱센 > 덧셈 순으로 계산 후 > 비교연산자 계산
        System.out.println(result); // false (8>9)

        result = (x + 2) * 3 > y; // 괄호안 덧셈 연산 후 괄호 밖 곱셈 계산 후 > 비교연산자 계산
        System.out.println(result); // true (12>9)

// 산술변환
        short j = 10;
        int k = 20;
        int l = j + k; // 결과값은 더 큰 표현타입인 int 타입의 변수로만 저장할 수 있습니다.
        long lx = 30L;
        long lz = l + lx; // 결과값은 더 큰 표현타입인 long 타입의 변수로만 저장할 수 있습니다.

        float fx = j; // 결과값은 더 큰 표현타입인 float 타입의 변수로만 저장할 수 있습니다.
        float fy = k; // 결과값은 더 큰 표현타입인 float 타입의 변수로만 저장할 수 있습니다.
        float fz = l; // 결과값은 더 큰 표현타입인 float 타입의 변수로만 저장할 수 있습니다.
        System.out.println(lz);
        System.out.println(fx);
        System.out.println(fy);
        System.out.println(fz);

// 비트 연산
        // 3의 이진수값은 11(2). 12의 이진수값은 1100(2).
        // (2) 표기는 이 숫자가 이진수값이라는 표식.

        System.out.println(3 << 2);
        // 3의 이진수값인 11(2) 에서 왼쪽으로 2번 옮겨져서 1100(2) 인 12값이 됩니다.


        System.out.println(3 >> 1);
        // 3의 이진수값인 11(2) 에서 오른쪽으로 1번 옮겨져서 1(2) 인 1 값이 됩니다.
        // 자릿수를 벗어난 비트는 버림.

    }
}
```
```console
15
6
2
8
2
2
0
0
1
6
8
6
30
10
200
2
0
true
true
false
false
true
false
false
true
true
true
false
true
true
true
false
true
false
true
true
false
false
true
false
true
12
10
20
10
0
0
0
12
10
20
10
0
11
9
21
10
10
10
11
121
false
정답
9
1
true
false
false
true
60
10.0
20.0
30.0
12
1
```

## IfStatement.java
```java
package week2;

import java.util.Objects;
import java.util.Scanner;

public class IfStatement {
    public static void main(String[] args) {
        // 조건문
        boolean flag = true;
        if (flag) {
            System.out.println("flag 값은 true 입니다."); // flag 값은 true 입니다. 출력
        }

        // 조건문 with else
        flag = false;
        if (flag) {
            System.out.println("flag 값은 true 입니다."); // 미출력
        } else {
            System.out.println("flag 값은 false 입니다."); // flag 값은 false 입니다. 출력
        }

        // 조건문 with else if
        int number = 2;
        if (number == 1) {
            System.out.println("number 값은 1 입니다."); // 미출력
        } else if (number == 2) {
            System.out.println("number 값은 2 입니다."); // number 값은 2 입니다. 출력
        } else {
            System.out.println("number 값은 모르는 값입니다."); // 미출력
        }

        // 중첩 조건문
        flag = true;
        number = 2;
        if (flag) {
            if (number == 1) {
                System.out.println("flag 값은 true, number 값은 1 입니다."); // 미출력
            } else if (number == 2) {
                System.out.println("flag 값은 true, number 값은 2 입니다."); // flag 값은 true, number 값은 2 입니다. 출력
            }
        } else {
            if (number == 1) {
                System.out.println("flag 값은 false, number 값은 1 입니다."); // 미출력
            } else if (number == 2) {
                System.out.println("flag 값은 false, number 값은 2 입니다."); // 미출력
            }
        }

        // 조건문으로 가위바위보 만들기
        // 입/출력 예시
        // A 입력 : 가위
        // B 입력 : 보
        // A 가 이겼습니다.
        Scanner sc = new Scanner(System.in);

        System.out.print("A 입력 : ");
        String aHand = sc.nextLine(); // A 입력

        System.out.print("B 입력 : ");
        String bHand = sc.nextLine(); // B 입력

        // 값을 비교하는 Objects.equals() 메서드 사용
        // 오버라이딩 해서 쓰는데 클래스로 선언하지 않아서 object를 쓴 것 같다.
        if (Objects.equals(aHand, "가위")) {
            if (Objects.equals(bHand, "가위")) {
                System.out.println("A 와 B 는 비겼습니다."); // A 와 B 의 입력값을 비교해서 결과 출력
            } else if (Objects.equals(bHand, "바위")) {
                System.out.println("B 가 이겼습니다.");
            } else if (Objects.equals(bHand, "보")) {
                System.out.println("A 가 이겼습니다.");
            } else {
                System.out.println(" B 유저 값을 잘못 입력하셨습니다.");
            }
        } else if (Objects.equals(aHand, "바위")) {
            if (Objects.equals(bHand, "가위")) {
                System.out.println("A 가 이겼습니다.");
            } else if (Objects.equals(bHand, "바위")) {
                System.out.println("A 와 B 는 비겼습니다.");
            } else if (Objects.equals(bHand, "보")) {
                System.out.println("B 가 이겼습니다.");
            }
        } else if (Objects.equals(aHand, "보")) {
            if (Objects.equals(bHand, "가위")) {
                System.out.println("B 가 이겼습니다.");
            } else if (Objects.equals(bHand, "바위")) {
                System.out.println("A 가 이겼습니다.");
            } else if (Objects.equals(bHand, "보")) {
                System.out.println("A 와 B 는 비겼습니다.");
            }
        }

    }
}
```
```console
flag 값은 true 입니다.
flag 값은 false 입니다.
number 값은 2 입니다.
flag 값은 true, number 값은 2 입니다.
A 입력 : 가위
B 입력 : 바위
B 가 이겼습니다.
```

## SwitchCase.java
```java
package week2;

public class SwitchCase {
    public static void main(String[] args) {
        // switch/case 문
        int month = 8;
        String monthString = "";
        switch (month) {
            case 1:
                monthString = "1월";
                break;
            case 2:
                monthString = "2월";
                break;
            case 3:
                monthString = "3월";
                break;
            case 4:
                monthString = "4월";
                break;
            case 5:
                monthString = "5월";
                break;
            case 6:
                monthString = "6월";
                break;
            case 7:
                monthString = "7월";
                break;
            case 8:
                monthString = "8월";
                break;
            case 9:
                monthString = "9월";
                break;
            case 10:
                monthString = "10월";
                break;
            case 11:
                monthString = "11월";
                break;
            case 12:
                monthString = "12월";
                break;
            default:
                monthString = "알수 없음";
        }
        System.out.println(monthString); // 8월 출력


        // if 로 변환
        if (month == 1) {
            monthString = "1월";
        } else if (month == 2) {
            monthString = "2월";
        } else if (month == 3) {
            monthString = "3월";
        } else if (month == 4) {
            monthString = "4월";
        } else if (month == 5) {
            monthString = "5월";
        } else if (month == 6) {
            monthString = "6월";
        } else if (month == 7) {
            monthString = "7월";
        } else if (month == 8) {
            monthString = "8월";
        } else if (month == 9) {
            monthString = "9월";
        } else if (month == 10) {
            monthString = "10월";
        } else if (month == 11) {
            monthString = "11월";
        } else if (month == 12) {
            monthString = "12월";
        } else {
            monthString = "알수 없음";
        }
        System.out.println(monthString); // 8월 출력

    }

}
```
```console
8월
8월
```

## ForStatement.java
```java
package week2;

public class forStatement {
    public static void main(String[] args) {
        // for 문
        // 출력: 0번째 출력, 1번째 출력, 2번째 출력, 3번째 출력
        for (int i = 0; i < 4; i++) { // 변수 i 값은 0 ~ 3 까지 반복
            System.out.println(i + "번째 출력"); // i 변수와 문자열 합치기
        }

        // 향상된 for 문
        // 출력: 3 6 9 12 15
        int[] numbers = {3, 6, 9, 12, 15};
        for (int number : numbers) {
            System.out.print(number + " ");
        }
        // 만약 기존 for 문으로 구현한다면?
        for (int i = 0; i < numbers.length; i++) { // 배열에 .length 를 붙이면 길이값이 응답됩니다.
            System.out.println(numbers[i]);
        }

        // while 문
        // 출력 : 1출력 2출력 3출력
        int number = 0;
        while (number < 3) {
            number++;
            System.out.println(number + "출력");
        }

        // do-while 문
        // 출력 : 4출력
        number = 4;
        do {
            System.out.println(number + "출력");
        } while (number < 3); // 연산을 한번 수행 후 조건문 체크


        // break 명령
        // 출력 : 1출력
        number = 0;
        while (number < 3) {
            number++;
            if (number == 2) {
                break;  // 2일때 반복 중단
            }
            System.out.println(number + "출력");
        }

        // break 명령 범위: break가 속한 반복문을 탈출.
        /* 출력
        i: 0 // 바깥 반복문 부터 수행 시작
        j: 0 // 안쪽 반복문 1회차 수행
        j: 1
        j: 2 // j 가 2일때 안쪽 반복문 break;
        i: 1 // 바깥 반복문은 아직 break; 호출이 안됬으므로 다음 반복수행
        j: 0 // 안쪽 반복문 2회차 수행
        j: 1
        j: 2 // j 가 2일때 안쪽 반복문 두번째 break;
        i: 2 // i 가 2일때 바깥 반복문도 break; 호출되어 종료*/
        for (int i = 0; i < 10; i++) {
            System.out.println("i: " + i);
            if (i == 2) {
                break; // i 가 2일때 가장 바깥 반복문이 종료됩니다.
            }
            for (int j = 0; j < 10; j++) {
                System.out.println("j: " + j);
                if (j == 2) {
                    break; // j 가 2일때 가장 안쪽 반복문이 종료됩니다.
                }
            }
        }


        // continue 명령
        // 출력: 1출력, 3출력
        number = 0;
        while (number < 3) {
            number++;
            if (number == 2) {
                continue;  // 2일때 반복 패스 = 출력 패스.
            }
            System.out.println(number + "출력");
        }


    }
}
```
```console
0번째 출력
1번째 출력
2번째 출력
3번째 출력
3 6 9 12 15 3
6
9
12
15
1출력
2출력
3출력
4출력
1출력
i: 0
j: 0
j: 1
j: 2
i: 1
j: 0
j: 1
j: 2
i: 2
1출력
3출력
```

## MultiplicationTable.java
```java
package week2;

import java.util.Scanner;

public class MultiplicationTable {
    public static void main(String[] args) {
        // 구구단 생성기
        /* 출력
        2곱하기2는4입니다.
        2곱하기3는6입니다.
        2곱하기4는8입니다.
        ... 중략 ...
        9곱하기8는72입니다.
        9곱하기9는81입니다.*/
        for (int i = 2; i <= 9; i++) { // 구구단 첫번째 지수 i
            for (int j = 2; j <= 9; j++) { // 구구단 두번째 지수 j
                System.out.println(i + "곱하기" + j + "는" + (i * j) + "입니다.");
            }
        }

        // 선택적 구구단 생성기
        // 입력단 제외
        // 입력: 2
        // 출력 - 입력값인 2단은 건너띄고 구구단 출력
        Scanner sc = new Scanner(System.in);
        int passNum = sc.nextInt(); // 출력제외할 구구단수 값
        for (int i = 2; i <= 9; i++) {
            if (i == passNum) {
                continue;
            }
            for (int j = 2; j <= 9; j++) {
                System.out.println(i + "곱하기" + j + "는" + (i * j) + "입니다.");
            }
        }

        // 입력단만 출력
        int printNum = sc.nextInt();
        for (int j = 2; j <= 9; j++) {
            System.out.println(printNum + "곱하기" + j + "는" + (printNum * j) + "입니다.");
        }


    }
}
```
```console
2곱하기2는4입니다.
2곱하기3는6입니다.
2곱하기4는8입니다.
2곱하기5는10입니다.
2곱하기6는12입니다.
2곱하기7는14입니다.
2곱하기8는16입니다.
2곱하기9는18입니다.
3곱하기2는6입니다.
3곱하기3는9입니다.
3곱하기4는12입니다.
3곱하기5는15입니다.
3곱하기6는18입니다.
3곱하기7는21입니다.
3곱하기8는24입니다.
3곱하기9는27입니다.
4곱하기2는8입니다.
4곱하기3는12입니다.
4곱하기4는16입니다.
4곱하기5는20입니다.
4곱하기6는24입니다.
4곱하기7는28입니다.
4곱하기8는32입니다.
4곱하기9는36입니다.
5곱하기2는10입니다.
5곱하기3는15입니다.
5곱하기4는20입니다.
5곱하기5는25입니다.
5곱하기6는30입니다.
5곱하기7는35입니다.
5곱하기8는40입니다.
5곱하기9는45입니다.
6곱하기2는12입니다.
6곱하기3는18입니다.
6곱하기4는24입니다.
6곱하기5는30입니다.
6곱하기6는36입니다.
6곱하기7는42입니다.
6곱하기8는48입니다.
6곱하기9는54입니다.
7곱하기2는14입니다.
7곱하기3는21입니다.
7곱하기4는28입니다.
7곱하기5는35입니다.
7곱하기6는42입니다.
7곱하기7는49입니다.
7곱하기8는56입니다.
7곱하기9는63입니다.
8곱하기2는16입니다.
8곱하기3는24입니다.
8곱하기4는32입니다.
8곱하기5는40입니다.
8곱하기6는48입니다.
8곱하기7는56입니다.
8곱하기8는64입니다.
8곱하기9는72입니다.
9곱하기2는18입니다.
9곱하기3는27입니다.
9곱하기4는36입니다.
9곱하기5는45입니다.
9곱하기6는54입니다.
9곱하기7는63입니다.
9곱하기8는72입니다.
9곱하기9는81입니다.
2
3곱하기2는6입니다.
3곱하기3는9입니다.
3곱하기4는12입니다.
3곱하기5는15입니다.
3곱하기6는18입니다.
3곱하기7는21입니다.
3곱하기8는24입니다.
3곱하기9는27입니다.
4곱하기2는8입니다.
4곱하기3는12입니다.
4곱하기4는16입니다.
4곱하기5는20입니다.
4곱하기6는24입니다.
4곱하기7는28입니다.
4곱하기8는32입니다.
4곱하기9는36입니다.
5곱하기2는10입니다.
5곱하기3는15입니다.
5곱하기4는20입니다.
5곱하기5는25입니다.
5곱하기6는30입니다.
5곱하기7는35입니다.
5곱하기8는40입니다.
5곱하기9는45입니다.
6곱하기2는12입니다.
6곱하기3는18입니다.
6곱하기4는24입니다.
6곱하기5는30입니다.
6곱하기6는36입니다.
6곱하기7는42입니다.
6곱하기8는48입니다.
6곱하기9는54입니다.
7곱하기2는14입니다.
7곱하기3는21입니다.
7곱하기4는28입니다.
7곱하기5는35입니다.
7곱하기6는42입니다.
7곱하기7는49입니다.
7곱하기8는56입니다.
7곱하기9는63입니다.
8곱하기2는16입니다.
8곱하기3는24입니다.
8곱하기4는32입니다.
8곱하기5는40입니다.
8곱하기6는48입니다.
8곱하기7는56입니다.
8곱하기8는64입니다.
8곱하기9는72입니다.
9곱하기2는18입니다.
9곱하기3는27입니다.
9곱하기4는36입니다.
9곱하기5는45입니다.
9곱하기6는54입니다.
9곱하기7는63입니다.
9곱하기8는72입니다.
9곱하기9는81입니다.
2
2곱하기2는4입니다.
2곱하기3는6입니다.
2곱하기4는8입니다.
2곱하기5는10입니다.
2곱하기6는12입니다.
2곱하기7는14입니다.
2곱하기8는16입니다.
2곱하기9는18입니다.
```

___


___
