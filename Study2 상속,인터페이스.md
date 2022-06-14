### Ch07.상속

#### 7.1 상속개념 ~ 7.3 부모 생성자 호출

✔유효선

➡ [상속(Inheritance) 개념](#상속inheritance-개념)

#### 7.4 메소드 재정의 ~ 7.6 protected 접근 제한자

✔김범우

➡ [자료](https://github.com/dakdlzhf/JavaStudy/blob/6333b4cc8c8c1517996306090c39a391095c7901/6%EC%9B%94%2012%EC%9D%BC%20%EB%A9%94%EC%86%8C%EB%93%9C~%EC%A0%91%EA%B7%BC%EC%9E%90.md)

#### 7.7 타입 변환과 다형성 ~ 7.8 추상 클래스

✔ 조아라

➡ [자료](https://github.com/ara0114/TIL/blob/d253a6af832039aca7792c34a97145d720db17ec/JAVA/TypeConversion,AbstractClass.md)

### Ch08.인터페이스

#### 8.1 인터페이스의 역할 ~ 8.4 인터페이스 사용

✔ 이학선

➡ [자료](https://github.com/gkrtjs406/TIL/blob/78eac469cbad8bfabd396a6d7977f86679fcc3d1/Java/인터페이스.md)

#### 8.5 타입 변환과 다형성 ~ 8.7 디폴트 메소드와 인터페이스 확장

✔오인웅

➡ [자료](https://github.com/mn00149/JavaStudy/blob/6da25828e31d271b36786e996f00e2f4f8cea345/study.md)

## [상속(Inheritance) 개념]()

자바에는 상속이라는 개념이 있다.

상속은 말그대로 부모클래스(상위클래스)가 자식클래스(하위클래스)에게 물려주는 것. (클래스확장)

단 , 부모는 자식클래스의 필드 및 메소드를 쓸 수 없다.

![상속](https://github.com/yhs0429/JavaStudy/blob/master/img/%EC%83%81%EC%86%8D%EA%B0%9C%EB%85%90.png)

---

### 상속의 장점

1. 기존 작성된 클래스를 재활용할 수 있기 때문에 효율적이고 개발시간을 줄여준다.
2. 중복된 코드를 줄이고 유지보수가 편하며 통일성 다형성을 구현할 수 있다.

---

### 클래스 상속

상속받을 자식의 클래스 명 뒤에 extends 키워드를 사용하고 부모클래스를 작성하면 된다.

자바에서 자식클래스가 여러 부모클래스로부터 상속받는건(다중상속) 불가능 하지만

부모클래스는 여러자식에게 상속할 수 있다.

단, 부모클래스의 private 접근 제한자를 가지고 있는 필드 및 메소드는 자식이 쓸수 없고 부모와 자식이 서로

다른 패키지에 존재한다면 부모클래스의 default 접근 제한자를 가지고 있는 필드 및 메소드를 자식이 쓸 수 없다.

```
//부모클래스
package com.company;

public class ParentCafe {
    String coffee;
    int price;

    public void printMenu() {
        System.out.println(coffee + "는 " + price + "원입니다.");
    }
}

//자식클래스
package com.company;

public class ChildCafe extends ParentCafe {
    // ChildCafe 가 ParentCafe 의 필드를 상속받아 사용할 수 있다.
    ChildCafe (String coffee, int price) {
        this.coffee = coffee;
        this.price = price;
    }
}

//메인클래스
package com.company;

public class Main {

    public static void main(String[] args) {
        ChildCafe child = new ChildCafe("아메리카노", 4100);

        child.printMenu();
    }
}
```

---

### 부모 생성자 호출

부모 없는 자식 없다!

- 자식 객체를 생성할 때는 부모 객체부터 생성되고 자식 객체가 생성된다.
- 부모 생성자가 호출 완료되고, 자식 생성자가 나중에 호출 완료된다.

#### 명시적으로 부모 생성자 호출

- 부모 객체를 생성할 때 , 부모 생성자를 선택해서 호출할 수 있다.

- super(매개값 , ... ) 은 매개값과 동일한 타입,개수, 순서가 맞는 부모 생성자를 호출한다.
- 반드시 자식 생성자의 첫줄에 위치해야 한다.
- 부모 클래스에 기본(매개변수 X) 생성자가 없다면 필수적으로 작성해야 한다.

```
//부모 클래스
public class people{
	public String name;
	public String ssn;

	public People(String name, String ssn){
		this.name = name;
		this.ssn = ssn;
	}
}
 // 부모 객체 생성 .

//자식 클래스
public class Student extends People{
	public int studentNo;

	public Student(String name, String ssn, int studentNo){
	super(name, ssn);      // 부모생성자 호출
	this.studentNo = studentNo;
	}
}

//메인 클래스
public class StudentExample{

	public static void main (String[]args){
	//생성자 호출 순서 : 1. 부모생성자 , 2. 자식 생성자
	Student student = new Student("홍길동", "123456-1231231" , 1);

	System.out.println("name : " + student.name);
	System.out.println("ssn : "+ student.ssn);
	//부모에서 물려받은 필드 출력
	System.out.println("studentNo : " + student.studentNo);
	}
}
```
