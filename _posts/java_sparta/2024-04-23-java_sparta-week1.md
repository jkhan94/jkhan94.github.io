---
layout: post
title: JAVA_sparta - wekk01
date: 2024-04-23
category: JAVA_sparta
---

## DataType.java
```java
package week1;

import java.util.Arrays;
import java.util.Scanner;

//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.
public class Main {
    public static void main(String[] args) {
        // 정수형
        byte byteNumber = 127; // byte 는 -128 ~ 127
        short shortNumber = 32767; // short 는 -32,768~32,767
        int intNumber = 2147483647; // int 는 -21억~21억
        long longNumber = 2147483647L; // long 은 숫자뒤에 알파벳 L 을 붙여서 표기.

        System.out.println(byteNumber);
        System.out.println(shortNumber);
        System.out.println(intNumber);
        System.out.println(longNumber);

        // 실수형
        float floatNumber = 1.123f; // float (4byte) : `3.4 * -10^38` ~ `3.4 * 10^38`. 소수점 7자리까지.
        double doubleNumber = 2.123123123; // double (8byte) :  `1.7 * -10^308` ~ `1.7 * 10^308` 소수점 16자리까지.

        System.out.println(floatNumber);
        System.out.println(doubleNumber);

        // 캐스팅
        System.out.println((float) intNumber);  // int -> float 형변환
        System.out.println((double) intNumber); // int -> double 형변환

        System.out.println("float ->  int: " + (int) floatNumber); // float -> int 형변환
        System.out.println("double ->  int: " + (int) doubleNumber); // double -> int 형변환

        // 자동 형변환 : 큰 타입 = 작은 타입
        byteNumber = 10;
        intNumber = byteNumber;    // byte -> int 형변환
        System.out.println(intNumber); // 10

        char charAlphabet = 'A';
        intNumber = charAlphabet;   // char -> int 형변환
        System.out.println("charAlphabet = 'A' -> int " + intNumber); // A의 유니코드 : 65

        intNumber = 100;
        longNumber = intNumber; // int -> number 형변환
        System.out.println("int 100 -> long " + longNumber); // 100

        intNumber = 200;
        doubleNumber = intNumber; // int -> double 형변환
        System.out.println(doubleNumber); // 200.0  (소수점이 추가된 실수출력)

        // 자동 형변환: 작은 타입, 큰 타입 연산
        intNumber = 10;
        doubleNumber = 5.5;
        double result = intNumber + doubleNumber; // result 에 15.5 저장됨 (int -> double)
        System.out.println("10 + 5.5 = " + result);

        int iResult = intNumber / 4; // iResult 에 2 저장됨 (int형 연산 -> 소수점 버려짐)
        double dResult = intNumber / 4.0; // dResult 에 2.5 저장됨 (double형 연산 -> 소수점 저장)
        System.out.println("iResult = " + iResult);
        System.out.println("dResult = " + dResult);

        // 배열
        int[] a = {1, 2, 3};
        System.out.println(a); // a에 저장된 주소
        System.out.println(Arrays.toString(a)); // [1, 2, 3] 출력.

        // 문자열
        String msg = "Hello World";
        System.out.println(msg);

        // 래퍼클래스
        // 박싱 : Integer 래퍼 클래스 num 에 21 의 값을 저장
        int number = 21;
        Integer num = number;

        // 언박싱
        int n = num.intValue(); // 래퍼 클래스들은 inValue() 같은 언박싱 메서드들을 제공.
        System.out.println("int number = " + number);
        System.out.println("Integer num = " + num);
        System.out.println("num.intValue() = " + n);

        /////////////////////////////////
        // 아스키코드
        // 숫자 -> 문자
        Scanner sc = new Scanner(System.in);
        int asciiNumber = sc.nextInt();
        char ch = (char) asciiNumber; // 문자로 형변환을 해주면 숫자에 맞는 문자로 표현됩니다.
        System.out.println(ch);

        // 문자 -> 숫자
        Scanner sc1 = new Scanner(System.in);
        char letter = sc1.nextLine().charAt(0); // 첫번째 글자만 받아오기위해 charAt(0) 메서드를 사용합니다.
        asciiNumber = (int) letter; // 숫자로 형변환을 해주면 저장되어있던 아스키 숫자값으로 표현됩니다.
        System.out.println(asciiNumber);

        sc.close();
        sc1.close();

    }
}
```
```console
127
32767
2147483647
2147483647
1.123
2.123123123
2.14748365E9
2.147483647E9
float ->  int: 1
double ->  int: 2
10
charAlphabet = 'A' -> int 65
int 100 -> long 100
200.0
10 + 5.5 = 15.5
iResult = 2
dResult = 2.5
[I@5f184fc6
[1, 2, 3]
Hello World
int number = 21
Integer num = 21
num.intValue() = 21
65
A
a
97
```

## recipe.java
```java
package week1;

import java.util.Scanner;

/* 요리 레시피 메모장 만들기
입력값
내가 좋아하는 요리 제목을 먼저 입력합니다.
요리 별점을 1~5 사이의 소수점이 있는 실수로 입력해 주세요. (ex. 3.5)
이어서 내가 좋아하는 요리 레시피를 한 문장씩 10문장을 입력합니다.

출력값
입력이 종료되면 요리 제목을 괄호로 감싸서 먼저 출력해 줍니다.
이어서, 요리 별점을 소수점을 제외한 정수로만 출력해 줍니다. (ex. 3)
바로 뒤에 정수 별점을 5점 만점 퍼센트로 표현했을 때 값을 실수로 출력해 줍니다. (ex. 60.0%)
이어서, 입력한 모든 문장 앞에 번호를 붙여서 모두 출력해 줍니다.

ex) 입력 예시
백종원 돼지고기 김치찌개 만들기
4.5
돼지고기는 핏물을 빼주세요.
잘익은 김치 한포기를 꺼내서 잘라주세요.
냄비에 들기름 적당히 두르고 김치를 넣고 볶아주세요.
다진마늘 한스푼, 설탕 한스푼 넣어주세요.
종이컵으로 물 8컵 부어서 센불에 끓여주세요.
핏물 뺀 돼지고기를 넣어주세요.
된장 반스푼, 양파 반개, 청양고추 한개를 썰어서 넣어주세요.
간장 두스푼반, 새우젓 두스푼, 고춧가루 두스푼반 넣어주세요.
중불로 줄여서 오래 끓여주세요~!!
마지막에 파 쏭쏭 썰어서 마무리하면 돼요^^

*
예시 출력
[ 백종원 돼지고기 김치찌개 만들기 ]
별점 : 4 (80.0%)
1. 돼지고기는 핏물을 빼주세요.
2. 잘익은 김치 한포기를 꺼내서 잘라주세요.
3. 냄비에 들기름 적당히 두르고 김치를 넣고 볶아주세요.
4. 다진마늘 한스푼, 설탕 한스푼 넣어주세요.
5. 종이컵으로 물 8컵 부어서 센불에 끓여주세요.
6. 핏물 뺀 돼지고기를 넣어주세요.
7. 된장 반스푼, 양파 반개, 청양고추 한개를 썰어서 넣어주세요.
8. 간장 두스푼반, 새우젓 두스푼, 고춧가루 두스푼반 넣어주세요.
9. 중불로 줄여서 오래 끓여주세요~!!
10. 마지막에 파 쏭쏭 썰어서 마무리하면 돼요^^
* */
public class recipe {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int lines = 10;
        String[] description = new String[lines];
        int stars = 5;

        System.out.println("Enter recipe name: ");
        String name = sc.nextLine();
        System.out.println("Enter recipe ratings: ");
        float rating = sc.nextFloat();
        System.out.println("Enter recipe description: ");
        // 버퍼 비우기
        if (sc.hasNext()) {
            sc.nextLine();
        }
        for (int i = 0; i < lines; i++) {
            description[i] = sc.nextLine();
        }

        System.out.println("[ " + name + " ]");
        // int형끼리 계산하면 결과가 int.
        System.out.println("별점 : "+(int) rating + " (" + ((int) rating / (double) stars * 100) + "%)");
        for (int i = 0; i < lines; i++) {
            System.out.println((i + 1) + ". " + description[i]);
        }

        sc.close();

    }
}
```
```console
Enter recipe name: 
백종원 돼지고기 김치찌개 만들기
Enter recipe ratings: 
4.5
Enter recipe description: 
돼지고기는 핏물을 빼주세요.
잘익은 김치 한포기를 꺼내서 잘라주세요.
냄비에 들기름 적당히 두르고 김치를 넣고 볶아주세요.
다진마늘 한스푼, 설탕 한스푼 넣어주세요.
종이컵으로 물 8컵 부어서 센불에 끓여주세요.
핏물 뺀 돼지고기를 넣어주세요.
된장 반스푼, 양파 반개, 청양고추 한개를 썰어서 넣어주세요.
간장 두스푼반, 새우젓 두스푼, 고춧가루 두스푼반 넣어주세요.
중불로 줄여서 오래 끓여주세요~!!
마지막에 파 쏭쏭 썰어서 마무리하면 돼요^^

[ 백종원 돼지고기 김치찌개 만들기 ]
별점 : 4 (80.0%)
1. 돼지고기는 핏물을 빼주세요.
2. 잘익은 김치 한포기를 꺼내서 잘라주세요.
3. 냄비에 들기름 적당히 두르고 김치를 넣고 볶아주세요.
4. 다진마늘 한스푼, 설탕 한스푼 넣어주세요.
5. 종이컵으로 물 8컵 부어서 센불에 끓여주세요.
6. 핏물 뺀 돼지고기를 넣어주세요.
7. 된장 반스푼, 양파 반개, 청양고추 한개를 썰어서 넣어주세요.
8. 간장 두스푼반, 새우젓 두스푼, 고춧가루 두스푼반 넣어주세요.
9. 중불로 줄여서 오래 끓여주세요~!!
10. 마지막에 파 쏭쏭 썰어서 마무리하면 돼요^^
```
		
