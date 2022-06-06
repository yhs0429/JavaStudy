# 객체 생성과 클래스 변수

![생성](https://github.com/yhs0429/JavaStudy/blob/master/img/%EA%B0%9D%EC%B2%B4%EC%83%9D%EC%84%B1.png)

- 클래스 선언 후 컴파일하면 객체를 생성할 설계도가 만들어진다.

- 클래스로 부터 객체를 생성하는 방법은 다음과 같이 new연산자를 사용하면 된다.



![힙영역](https://github.com/yhs0429/JavaStudy/blob/master/img/%ED%9E%99%EC%98%81%EC%97%AD.png)

- new는 클래스로부터 객체를 생성하는 연산자이다.
- new 연산자 뒤에는 생성자가 온다, 생성자는 클래스() 형태를 가지고 있음.
- new 연산자로 생성된 객체는 힙(heep)영역에 생성된다, 생성 후 객체의 주소를 리턴한다.
- 리턴 한 주소를 참조 타입인 클래스 변수에 저장하면 변수를 통해 객체를 사용할 수 있다.