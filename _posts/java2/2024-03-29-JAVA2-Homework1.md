---
layout: post
title: JAVA2 - Homework1
date: 2024-03-29
category: JAVA2
---

## User.java
```java
package homework;

public class User {
	// 1. User 클래스

	// 필드
	// 아이디 id
	// 비밀번호 pw
	// 이름 name
	// 이메일 주소 email
	// 로그인 상태 loginState
	String id;
	String pw;
	String name;
	String email;
	// boolean형 디폴트값은 false
	// 명시적 초기화는 디폴트가 아닌 값으로 초기화 할 떄 사용
	boolean loginState;
//	boolean loginState = false;

	// 생성자
	// 매개변수가 없는 생성자
	// String id, String pw, String name, String email 를 매개변수로 받는 생성자
	public User() {
		super();
	}

	public User(String id, String pw, String name, String email) {
		super();
		this.id = id;
		this.pw = pw;
		this.name = name;
		this.email = email;
	}

	// 메소드
	// 로그인 메소드 (아이디와 비밀번호를 입력받아 기존 아이디와 비밀번호와 일치하면 로그인 성공, 아니면 로그인 실패 출력, 로그인 성공시
	// loginState 값을 true로 변경)
	void login(String id, String pw) {
		if ((this.id).equals(id) && this.pw == pw) {
			System.out.println("로그인 성공");
			this.loginState = true;
		} else {
			System.out.println("로그인 실패");
		}
	}

	// 로그아웃 메소드 (loginState 가 true 일 경우 false로 변경후 안녕히 가세요 출력, false일 경우 로그인 상태가
	void logout() {
		// this.loginState == true는 쓰지 않음
		// this.loginState는 boolean형으로 
		// 참일 때는 this.loginState
		// 거짓일 때는 !this.loginState으로 사용하는 게 보편적
		if (this.loginState) {
			this.loginState = false;
			System.out.println("안녕히 가세요");
		} else if (this.loginState == false) {
			System.out.println("로그인 상태가 아닙니다");
		}
	}

	// 회원 정보 조회 메소드 (loginState 값이 true 일 경우 가입된 정보를 출력, false일 경우 로그인 상태가 아닙니다 출력)
	void getData() {
		if (this.loginState == true) {
			System.out.println("회원 정보 출력");
			System.out.println("ID : " + this.id);
			System.out.println("이름 : " + this.name);
			System.out.println("이메일 주소 : " + this.email);
		} else if (this.loginState == false) {
			System.out.println("로그인 상태가 아닙니다");
		}
	}

}
```

## Buyer.java
```java
package homework;

public class Buyer extends User {
	// 2. Seller 클래스 (User 클래스를 상속받는다)

	// 필드
	// 주소 address
	String address;

	// 생성자
	// 매개변수가 없는 생성자
	// String id, String pw, String name, String email, String address 를 매개변수로 받는
	// 생성자
	// 상속받은 필드는 부모 생성자를 통해 초기화 한다
	public Buyer() {
		super();
	}

	public Buyer(String id, String pw, String name, String email, String address) {
		super(id, pw, name, email);
		this.address = address;
	}

	// 메소드
	// 비밀번호 찾기 메소드 (아이디를 입력받아 기존 아이디와 일치하면 비밀번호 출력)
	void findPw(String id) {
		if ((this.id).equals(id)) {
			System.out.println("\nBuyer 비밀번호는 " + this.pw + " 입니다.");
		}
	}

	// 회원 정보 조회 메소드 (재정의하여 주소도 출력한다)
	// alt + shift + s + v
	@Override
	void getData() {
		// 부모클래스의 getData를 쓰지 않음
//		super.getData();
		// 자식ㅋ클래스에서 전부 재정의
		if (this.loginState) {
			System.out.println("\nBuyer 회원 정보 출력");
			System.out.println("ID : " + this.id);
			System.out.println("이름 : " + this.name);
			System.out.println("이메일 주소 : " + this.email);
			System.out.println("주소 : " + this.address);
		} else if (!this.loginState) {
			System.out.println("\nBuyer 로그인 상태가 아닙니다");
		}
	}

}
```

## Seller.java
```java
package homework;

public class Seller extends User {
	// 3. Buyer 클래스 (User 클래스를 상속받는다)

	// 필드
	// 판매자 번호 sellerNumber
	// 판매자명 sellerName
	int sellerNumber;
	String sellerName;

	// 생성자
	// 매개변수가 없는 생성자
	// String id, String pw, String name, String email, int sellerNumber, String
	// sellerName 를 매개변수로 받는 생성자
	// 상속받은 필드는 부모 생성자를 통해 초기화 한다
	public Seller() {
		super();
	}

	public Seller(String id, String pw, String name, String email, int sellerNumber, String sellerName) {
		super(id, pw, name, email);
		this.sellerNumber = sellerNumber;
		this.sellerName = sellerName;
	}

	// 메소드
	// 비밀번호 찾기 메소드 (아이디와 판매자 번호를 입력받아 기존의 정보와 일치하면 비밀번호를 출력)
	void findPw(String id, int sellerNumber) {
		if ((this.id).equals(id) && this.sellerNumber == sellerNumber) {
			System.out.println("\nSeller 비밀번호는 " + this.pw + " 입니다.");
		}
	}

	// 회원 정보 조회 메소드 (재정의하여 판매자명, 판매자번호도 출력한다)
	@Override
	void getData() {
		// 부모클래스의 getData() 함수 호출
//		super.getData();
		// 자식클래스에서 추가되는 부분만 재정의
		if (this.loginState) {
			System.out.println("\nSeller 회원 정보 출력");
			System.out.println("판매자명 : " + this.sellerName);
			System.out.println("판매자번호 : " + this.sellerNumber);
		} else if (!this.loginState) {
			System.out.println("\nSeller 로그인 상태가 아닙니다");
		}
	}

}
```

## Homework1.java
```java
// 요구사항에 맞추어 어떻게 설계를 하고 코드를 작성할 것인가가 포인트인 문제였습니다
package homework;

public class Homework1 {

	// 아래의 메소드를 완성시키세요 (매개변수, 실행할 코드)
	void method1(User user) {
		// 로그인 메소드 사용
		user.login(user.id, user.pw);
	}

	void method2(User user) {
		// 회원 정보 조회 메소드 사용
		user.getData();
	}

	void method3(User user) {
		// 비밀번호 찾기 메소드 사용
		if (user instanceof Buyer) {
			((Buyer) user).findPw(user.id);
		} else if (user instanceof Seller) {
			((Seller) user).findPw(user.id, ((Seller) user).sellerNumber);
		}

	}

//	void method1(Buyer buyer, Seller seller) {
//		// 로그인 메소드 사용
//		if (buyer != null) {
//			buyer.login(buyer.id, buyer.pw);
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//		if (seller != null) {
//			seller.login(seller.id, seller.pw);
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//	}
//
//	void method2(Buyer buyer, Seller seller) {
//		// 회원 정보 조회 메소드 사용
//		if (buyer != null) {
//			buyer.getData();
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//		if (seller != null) {
//			seller.getData();
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//	}
//
//	void method3(Buyer buyer, Seller seller) {
//		// 비밀번호 찾기 메소드 사용
//		if (buyer != null) {
//			buyer.findPw(buyer.id);
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//		if (seller != null) {
//			seller.findPw(seller.id, seller.sellerNumber);
//		} else {
//			System.out.println("아이디와 비밀번호를 제대로 입력해주세요!");
//		}
//	}

	public static void main(String[] args) {

		// 1. User 클래스

		// 필드
		// 아이디 id
		// 비밀번호 pw
		// 이름 name
		// 이메일 주소 email
		// 로그인 상태 loginState

		// 생성자
		// 매개변수가 없는 생성자
		// String id, String pw, String name, String email 를 매개변수로 받는 생성자

		// 메소드
		// 로그인 메소드 (아이디와 비밀번호를 입력받아 기존 아이디와 비밀번호와 일치하면 로그인 성공, 아니면 로그인 실패 출력, 로그인 성공시
		// loginState 값을 true로 변경)
		// 로그아웃 메소드 (loginState 가 true 일 경우 false로 변경후 안녕히 가세요 출력, false일 경우 로그인 상태가
		// 회원 정보 조회 메소드 (loginState 값이 true 일 경우 가입된 정보를 출력, false일 경우 로그인 상태가 아닙니다 출력)

		// 2. Buyer 클래스 (User 클래스를 상속받는다)

		// 필드
		// 주소 address

		// 생성자
		// 매개변수가 없는 생성자
		// String id, String pw, String name, String email, String address 를 매개변수로 받는
		// 생성자
		// 상속받은 필드는 부모 생성자를 통해 초기화 한다

		// 메소드
		// 비밀번호 찾기 메소드 (아이디를 입력받아 기존 아이디와 일치하면 비밀번호 출력)
		// 회원 정보 조회 메소드 (재정의하여 주소도 출력한다)

		// 3. Seller 클래스 (User 클래스를 상속받는다)

		// 필드
		// 판매자 번호 sellerNumber
		// 판매자명 sellerName

		// 생성자
		// 매개변수가 없는 생성자
		// String id, String pw, String name, String email, int sellerNumber, String
		// sellerName 를 매개변수로 받는 생성자
		// 상속받은 필드는 부모 생성자를 통해 초기화 한다

		// 메소드
		// 비밀번호 찾기 메소드 (아이디와 판매자 번호를 입력받아 기존의 정보와 일치하면 비밀번호를 출력)
		// 회원 정보 조회 메소드 (재정의하여 판매자명, 판매자번호도 출력한다)

		Homework1 hw = new Homework1();
		// Buyer, Seller 클래스명이 서로 바뀐 것 같아 변경했습니다.
		Buyer buyer = new Buyer("user1", "user1", "b1234", "b1234@b1234.com", "서울시 강남구 역삼동");
		Seller seller = new Seller("user2", "user2", "s1234", "s1234@b1234.com", 1, "자바상점");

		hw.method1(buyer);
		hw.method2(buyer);
		hw.method3(buyer);
		
		System.out.println("\n///////\n");
		
		hw.method1(seller);
		hw.method2(seller);
		hw.method3(seller);

	}

}
```
```console
로그인 성공

Buyer 회원 정보 출력
ID : user1
이름 : b1234
이메일 주소 : b1234@b1234.com
주소 : 서울시 강남구 역삼동

Buyer 비밀번호는 user1 입니다.

///////

로그인 성공

Seller 회원 정보 출력
판매자명 : 자바상점
판매자번호 : 1

Seller 비밀번호는 user2 입니다.
```
		
