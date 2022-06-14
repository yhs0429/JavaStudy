### [06] 클래스

#### 6.1 객체지향프로그래밍 ~ 6.3 클래스선언

✔조아라

➡[자료](https://github.com/ara0114/TIL/blob/40f2e7b1517be7f4e3e24de6816ef7f023c2e470/JAVA/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D.md)

#### 6.4 객체생성과 클래스변수 ~ 6.6 필드

✔유효선

➡ [자료](https://github.com/yhs0429/JavaStudy/blob/46678cf4ec569dabd41b8f1ae2ad782871ec908c/Study1 Class.md)

#### 6.7 생성자 ~ 6.9 인스턴스 멤버와 this

✔김범우

➡ [자료](https://github.com/dakdlzhf/JavaStudy/blob/6333b4cc8c8c1517996306090c39a391095c7901/6월 6일 생성자~메소드.md)

#### 6.10 정적멤버와 static ~ 6.12 패키지

✔ 오인웅

➡ [자료](https://github.com/mn00149/JavaStudy/blob/6da25828e31d271b36786e996f00e2f4f8cea345/study.md)

#### 6.13 접근제한자 ~ 6.15 어노테이션

✔ 이학선

➡ [자료](https://github.com/gkrtjs406/TIL/blob/78eac469cbad8bfabd396a6d7977f86679fcc3d1/Java/클래스(객체지향프로그래밍).md)

## 객체 생성과 클래스 변수

![생성](https://github.com/yhs0429/JavaStudy/blob/master/img/%EA%B0%9D%EC%B2%B4%EC%83%9D%EC%84%B1.png)

- 클래스 선언 후 컴파일하면 객체를 생성할 설계도가 만들어진다.

- 클래스로 부터 객체를 생성하는 방법은 다음과 같이 new연산자를 사용하면 된다.
- new 연산자 뒤에는 생성자가 온다, 생성자는 클래스() 형태를 가지고 있다.

![힙영역](https://github.com/yhs0429/JavaStudy/blob/master/img/%ED%9E%99%EC%98%81%EC%97%AD.png)

- new 연산자로 생성된 객체는 힙(heep)영역에 생성된다, 생성 후 객체의 주소를 리턴한다.
- 리턴 한 주소를 참조 타입인 클래스 변수에 저장하면 변수를 통해 객체를 사용할 수 있다.

![변수객체](https://github.com/yhs0429/JavaStudy/blob/master/img/%EB%B3%80%EC%88%98%EA%B0%9D%EC%B2%B4%EC%83%9D%EC%84%B1.png)

- Car 클래스는 하나지만 new연산자를 사용한 만큼 객체가 메모리에 생성됨 ,

  이러한 객체들은 Car클래스의 인스턴스 이다.

- 같은 클래스로부터 생성되었지만 각각의 Car객체는 완전히 독립된 서로 다른 객체임.**(결과값)**



## 클래스의 구성멤버

![구성멤버](https://github.com/yhs0429/JavaStudy/blob/master/img/%EA%B5%AC%EC%84%B1%EB%A9%A4%EB%B2%84.png)

- 클래스에는 객체가 가져야 할 구성 멤버가 선언된다 (필드,생성자,메소드) 

  이 구성 멤버들은 생략되거나 복수 개가 작성될 수 있다.

- 필드(Field)

  - 객체의 데이터가 저장되는 곳

- 생성자(Constructor)
  - 객체 생성시 초기화 역활 담당
- 메소드(Method)
  - 객체의 동작에 해당하는 실행 블록

---

**필드**

- 필드는 객체의 고유 데이터, 부품객체 , 상태정보를 저장하는 곳.
- 선언 형태는 변수와 비스하지만 필드를 변수라고 부르지않음.

​		(변수는 생성자와 메소드 내에서만 사용되고 생성자와 메소드가 실행 종료되면 자동소멸됨)

- 필드는 생성자와 메소드 전체에서 사용되며 객체가 소멸되지 않는 한 객체와 함께 존재함.

```
public class Car {
	// 고유데이터
	String company = "벤츠";
	String model = "C63";
	String color = "블랙";
	int maxSpeed = 330;
	
	//상태 데이터
	int speed;
	int rpm;
}
```

- 필드의 초기값은 필드선언 시 주어질수도 있고 , 생략될수도 있음.
- 초기값 지정 안된 필드들은 객체 생성 시 자동으로 기본 초기값으로 설정됨.

![초기값](https://github.com/yhs0429/JavaStudy/blob/master/img/%ED%95%84%EB%93%9C%20%EC%B4%88%EA%B8%B0%EA%B0%92.png)



**필드 사용**

```
public class CarExam{
	public static void main(String[] args) {
	//객체 생성
	Car car = new Car();
	
	//필드값 읽기
	System.out.println("제작회사 :"+car.company);
	System.out.println("모델명 :"+car.model);
	System.out.println("색깔 :"+car.color);
	System.out.println("최고속도 :"+car.maxSpeed);
	
	//필드값 변경
	car.speed = 150;
	car.rpm = 2000;
	System.out.println("수정된속도 :" +car.speed);
	System.out.println("수정된 엔진회전 수 :" +car.rpm);
	}
}
```

- 사용방법은 변수와 동일하지만 변수는 자신이 선언된 생성자, 메소드 블록 내부에서만 사용할수 있는 반면

  필드는 생성자와 모든 메소드에서 사용 가능.

- 필드값을 사용하기 위해 우선 Car객체를 생성한다.

---

**생성자**

- 생성자는 new 연산자로 호출되는 특별한 중괄호{} 블록

- 생성자의 역활은 객체 생성 시 초기화를 담당함,

  필드를 초기화 하거나 메소드를 호출해서 객체를 사용할 준비.

- 메소드와 비슷하게 생겼지만 클래스 이름으로 되어있고 리턴 타입이 없다.

---

**메소드**

- 메소드는 객체의 동작에 해당하는 중괄호{} 블록이다, 중괄호 블록은 메소드 이름을 가지고 있음.
- 메소드를 호출하면 중괄호 블록에 있는 모든 코드가 실행됨.
- 필드를 읽고,수정하는 역활도 하지만 다른객체를 생성해서 다양한 기능을 수행함.
- 객체 간의 데이터 전달의 수단으로 사용되며 외부로부터 매개값을 받을수도있고 실행 후 값을 리턴할수도있음
