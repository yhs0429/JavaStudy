### Ch13.제네릭

✔이학선

➡[13.2~3 제네릭타입, 멀티타입파라미터](https://github.com/gkrtjs406/TIL/blob/master/Java/%EC%A0%9C%EB%84%A4%EB%A6%AD(Generic).md)

✔유효선

➡[제네릭 메소드](#제네릭-메소드tr-r-methodt-t)

✔김범우

➡[13.6~7 와일드카드타입 , 제네릭 타입의 상속과 구현](https://github.com/dakdlzhf/JavaGroupStudy/blob/master/%EA%B9%80%EB%B2%94%EC%9A%B0/3%EC%A3%BC%EC%B0%A8.md)

✔조아라

➡[14.1~2 람다식 기분 문법](https://github.com/ara0114/TIL/blob/22069a756ba7e15ac7b5e674b85d394f835ec5ac/JAVA/LambdaExpression.md)

✔오인웅

➡[14.3~4 타겟타입 함수적 인터페이스, 클래스멤버와 로컬변수](https://github.com/mn00149/JavaStudy/blob/master/study.md)

✔임다빈

➡[14.5~6 표준 API의 함수적인터페이스 , 메소드참조](https://github.com/olabeann/JavaStudy/blob/master/0627%20%EB%9E%8C%EB%8B%A4%EC%8B%9D_%ED%95%A8%EC%88%98%EC%A0%81%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4_%20%EB%A9%94%EC%86%8C%EB%93%9C%20%EC%B0%B8%EC%A1%B0.md)

## 제네릭 메소드(<T,R> R method(T t))

**제네릭 메소드는 매개타입과 리턴 타입으로 타입 파라미터를 갖는 메소드** 를 말한다.

선언하는 방법은 리턴 타입 앞 <> 기호 추가 후 타입 파라미터를 기술한 다음, 

리턴 타입과 매개 타입으로 타입 파라미터를 사용하면 된다.

```
public <타입파라미터,> 리턴타입 메소드명(매개변수,) 
```

```
public <T> Box<T> boxing(T t)
```

boxing() 제네릭 메소드는 <> 기호 안에 T 기술한 뒤 , 

매개 변수 타입으로 T를 사용했고, 

리턴타입으로 제네릭 타입Box<T>를 사용



### 제네릭 메소드 호출

---

제네릭 메소드는 **두 가지 방식으로 호출** 가능.

- 코드에서 타입 파라미터의 구체적인 타입을 명시적으로 지정
- 컴파일러가 매개값의 타입을 보고 구체적인 타입을 추정하도록 할 수 있다

```
리턴타입 변수 = <구체적타입> 메소드명(매개값); // 명시적으로 구체적 타입을 지정  많이사용안함?
Box<Integer> box = <Integer>boxing(100);

리턴타입 변수 = 메소드명(매개값); 			//매개값을 보고 구체적 타입을 추정
Box<Integer> box = boxing(100);
```



예제 1

Util 클래스에서 정적 제네릭 메소드로 boxing()을 정의하고 BoxingMethodExample 클래스에서 호출

```
public class Box<T>{
	private T t;
	
	public void set(T t){
	this.t = t;
	}
	
	public T get(){
	return t;
	}
}
```

```
public class Util{
	public static <T> Box<T> boxing(T t){
		Box<T> box = new Box<T>();
		box.set(t);
		return box;
	}
}
```

```
public class BoxingMethodExample {
	public static void main(String[]args){
		Box<Integer> box1 = Util.<Integer>boxing(100);  //구체적 타입 명시
		int intValue = box1.get();
		//System.out.println(intValue);
		
		Box<String> box2 = Util.boxing("홍길동");		 //구체적 타입 추정
		String strValue = box2.get();
		//System.out.println(strValue);
	}
}
```



## 제한된 타입 파라미터(<T extends 최상위타입>)

타입 파라미터에 지정되는 구체적인 타입을 제한할 필요가 종종 있음.

예를 들면 숫자연산하는 제네릭 메소드는 매개값으로 Number타입 또는 

하위클래스타입 (Byte,Integer,Double..)의 인스턴스만 가져야 해서 제한된 타입 파라미터가 필요하다.



### 제한된 타입 파라미터 선언

---

**타입 파라미터 뒤에 extends 키워드를 붙이고 상위 타입을 명시**한다

상위 타입은 클래스뿐만 아니라 인터페이스도 가능하다. 

**인터페이스도 똑같이 extends**를 사용한다.(implements X)

```
public <T extends상위타입(클래스,인터페이스)> 리턴타입 메소드(매개변수){

}
```



### 타입 파라미터를 대체할 구체적인 타입

---

상위타입(클래스)이거나 하위 또는 구현 클래스(인터페이스)만 지정 할수 있다.

📌주의할점 :

메소드의 중괄호{} 안에서 타입 파라미터 변수로 사용 가능한 것은 상위 타입의 멤버(필드,메소드)로 제한된다.

**하위 타입에만** 있는 필드와 메소드는 사용할 수 없다.

```
public <T extends Number> int compare(T t1,T t2){
	double v1 = t1.doubleValue();  // Number 클래스의 doubleValue() 메소드 사용
	double v2 = t2.doubleValue();  // Number 클래스의 doubleValue() 메소드 사용
	return Double.compare(v1,v2);  // Number 클래스의 Double.compare() 메소드 사용
}
```

