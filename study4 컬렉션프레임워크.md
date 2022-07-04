✔유효선

➡[List컬렉션](#list-컬렉션)

✔오인웅

➡[]()

✔조아라

➡[]()

✔이학선

➡[]()

✔김범우

➡[]()

## List 컬렉션

**List 컬렉션은 객체를 일렬로 늘어놓은 구조**를 가지고 있다. 

객체를 인덱스로 관리하기 때문에 객체를 저장하면 자동 인덱스가 부여된다.

인덱스는 객체를 검색,삭제 할 때 사용하며 **List 컬렉션은 객체자체를 저장하는 것이 아닌 객체의 번지를 참조한다**.

동일한 객체를 중복 저장할 수 있는데 이때는 동일한 번지가 참조된다.

null을 저장할때는 해당 인덱스는 객체를 참조하지 않는다.

![image](https://user-images.githubusercontent.com/103401972/176923470-56ca994a-b6a0-42f9-af61-eb90e36b1fa7.png)



List 컬렉션에는 ArrayList, Vector, LinkedList 등이 있는데, 다음은 List 컬렉션에서 공통적으로 사용 가능한 List 인터페이스의 메소드들이다. 인덱스로 객체를 관리하기 때문에 인덱스를 매개값으로 갖는 메소드가 많다.

![image](https://user-images.githubusercontent.com/103401972/176936808-98aaf231-26f3-4228-a8c0-2bab621181ad.png)

위 표에서 메소드의 매개 변수 타입과 리턴 타입에 있는 E라는 타입 파라미터가 있는데, 이것은 List 인터페이스가 제네릭 타입이기 때문.

구체적인 타입은 구현 객체를 생성할 때 결정된다 .

객체 추가는 add() , 객체 찾아올때는 get() , 객체 삭제할때는 remove() 메소드를 사용한다.



```
List<String> list = ... ; 

list.add("홍길동"); // String 객체 저장
list.add(1, "신용권"); // 지정된 인덱스에 객체 삽입
String str = list.get(1); //인덱스 1에 담김 객체 찾기
list.remove(0) //인덱스 0에 담긴 객체 삭제
list.remove("신용권"); //해당 객체 삭제

for(String value : list) { 
    System.out.println(value);
} // List에 저장된 모든 객체를 얻어서 콘솔창에 출력
```

List 컬렉션에 저장되는 구체적인 타입을 String 으로 정해놓고, 추가, 삽입, 찾기,삭제하는 방법



```
List<String> list = ... ;
for(int i = 0; i < list.size(); i++) { 저장된총객체수만큼루핑
	String str = list.get(i);
}					// i인덱스에 저장된 String 객체를 가져옴
```

만약 전체 객체를 대상으로 하나씩 반복해서 저장된 객체를 얻고 싶다면 다음과 같이 for문을 사용할 수 있다.



```
				//list에 저장된 String 객체를 하나씩 가져옴
for(String str : list){ // 저장된 총 객체수만큼 루핑
}
```

인덱스가 필요 없다면 향상된 for문을 이용하는 것이 더욱 편리하다.



## ArrayList

ArrayList는 List 인터페이스의 구현 클래스로 ArrayList에 객체를 추가하면 객체가 인덱스로 관리된다. 

일반 배열과 ArrayList는 인덱스로 객체를 관리한다는 점에서는 유사하지만, 큰 차이점을 가지고 있다. 

배열은 생성할 때 크기가 고정되고 사용 중에 크기를 변경할 수 없지만 ArrayList는 저장 용량(capacity)을 초과한 객체들이 들어오면 자동으로 저장 용량(capacity)이 늘어난다는 것이다.  

다음은 ArrayList 객체의 내부 구조를 보여준다.

![image](https://user-images.githubusercontent.com/103401972/177054655-df9ba6b9-3d96-4675-8eeb-dd5660b63cb6.png)



ArrayList를 생성하기 위해서는 저장할 객체 타입을 타입 파라미터로 표기하고 기본 생성자를 호출하면 된다.

```
List<String> list = new ArrayList();
//String을 저장하는 ArrayList (기본저장용량 10)
```

기본 생성자로 ArrayList 객체를 생성하면 내부에 10개의 객체를 저장할 수 있는 초기용량을 가지게 됨. 저장되는 객체 수가 늘어나면 용량이 자동으로 증가하지만, 처음부터 용량을 크게 잡고 싶다면 용량크기를 매개값으로 받는 생성자를 이용하면 된다.

```
List<String>list = new ArrayList<String>(30);
//String 객체 30개를 저장할 수 있는 용량을 가짐
```



```
// 자바 4 이전까지는 타입 파라미터가 없었기 때문에 아래코드 같이 ArrayList를 생성했다. 
// 타입을 변환시켜줘야함 (귀찮,성능 down)
 List list = new ArrayList();
 list.add("블로그");
 Object obj = list.get(0);
 String blog = (String) obj;
 
// 자바5 이후

List<String> list = new ArrayList<String>();
list.add("블로그");
String blog = list.get(0);
```

ArrayList에 객체를 추가하면 인덱스 0 부터 차례대로 저장된다. ArrayList에서 특정 인덱스의 객체를 제거 하면 바

로 뒤 인덱스부터 마지막 인덱스까지 모두 앞으로 1씩 당겨지고 특정 인덱스에 객체를 삽입하면 해당 인덱스로부터 모두 1씩 밀려난다.

따라서 빈번한 **객체 삭제와 삽입이 일어나는 곳**에서는 ArrayList를 사용하는 것이 바람직하지 않다.

그러나 **인덱스 검색이나 맨 마지막에 객체를 추가**하는 경우에는 ArrayList를 사용한다.

```
public class ArrayList1{
	public static void main(String[] args){
	List<String>list = new ArrayList<String>();
	list.add("java");
	list.add("자바");
	list.add("개발에만 집중");
	list.add(1,"중간에 추가하기")
	
	int size = list.size(); // 저장된 총 객체 수
	System.out.println("리스트 인덱스 갯수: "+size);// 4
	
	String list_value = list.get(1); // 1번 인덱스 검색
	System.out.println("1번 인덱스에 있는 값: "+list.get(1)); // 중간에 추가하기
	
	for(int i=0; i<list.size(); i++){ // 저장된 총 객체수만큼 루핑
		list_Value = list.get(i);
        System.out.println(i+ ":" + list.Value);
        //0:java
        //1:중간에 추가하기
        //2:자바
        //3:개발에만 집중
        }
        list.remove(2); //삭제
        
        for(int i =0; i<list.size(); i++){
        	list_Value = list.get(i);
        	System.out.println(i+ ":" + list_Value);
        	//0:java
        	//1:중간에 추가하기
        	//2:개발에만 집중
        }
	}
}
```

ArrayList를 생성하고 런타임 시 필요에 의해 객체들을 추가하는 것이 일반적이지만, 고정된 객체들로 구성된 List를 생성할 때도 있다. 이런 경우  **Arrays.asList(T...a)메소드**를 사용하는 것이 간편하다.

```
List<T> list = Arrays.asList(T...a)
```

T타입 파라미터에 맞게 asList()의 매개값을 순차적으로 입력하거나 , T[]배열을 매개값으로 주면된다.

```
public class ArrayList2{
	public static void main(String[]args){
		List<String>list = Arrays.asList("트와이스","잇지","아이오아이");
		for(String idol : list){
			System.out.println(idol);
			//트와이스
			//잇지
			//아이오아이
		}
	}
}
```



## Vector

Vector는 ArrayList와 동일한 내부 구조를 가지고 있다.Vector를 생성하기 위해서는 저장할 객체타입을 타입 파라미터로 표기하고 기본 생성자를 호출하면 된다.

```
List<E> list = new Vector<E>();
```

ArrayList와 다른점은 Vector는 동기화된 메소드로 구성되어 있기 때문에 **멀티스레드가 동시에 이 메소드들을 실행할 수 없고**, 하나의 스레드가 실행을 완료해야만 다른 스레드를 실행할 수 있다. 그래서 멀티 스레드 환경에서 안전하게 객체를 추가, 삭제할 수 있다. 다만 동기화되어 있기 때문에 ArrayList보다는 객체를 추가, 삭제하는 과정은 느릴수 밖에 없다. 안전성을 추구하는데 있어서 속도를 포기한 트레이드 오프이다.

```
public class VectorExample {

	public static void main(String[] args) {
		
		List<Board> list = new Vector<Board>();
		list.add(new Board("제목1", "내용1", "글쓴이1"));
		list.add(new Board("제목2", "내용2", "글쓴이2"));
		list.add(new Board("제목3", "내용3", "글쓴이3"));
		list.add(new Board("제목4", "내용4", "글쓴이4"));
		list.add(new Board("제목5", "내용5", "글쓴이5"));
		//list.add(new Board("한 개는 불가능"));
		
		list.remove(2); //2번 인덱스 삭제 (뒤 인덱스들 1씩당겨짐)
		list.remove(3); 

		for(int i = 0; i < list.size(); i++ ) {
			Board board = list.get(i);
			System.out.println( board.subject + "\t" + board.content + "\t" + board.writer);
			//제목1 내용1 글쓴이1
			//제목2 내용2 글쓴이2
			//제목4 내용4 글쓴이4
		}	
	}
}
```

```
public class Board {

	String subject;
	String content;
	String writer;
	
	public Board(String subject, String content, String writer) {
	
		this.subject = subject;
		this.content = content;
		this.writer = writer;
	}
	//Board객체가 생성될 때 실행되는 생성자(Constructor)이다.
	

}
```

