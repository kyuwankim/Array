배열 컬랙션


## 접근제한자


### public

외부의 클래스로부터의 접근을 완전히 허용하는 수식어로서 main() 메소드는 외부에서 접근이 가능해야 하므로 반드시 public 으로 선언하여야 한다.

또한, 웹에서 불특정 다수의 접근을 허용해야 하는 Applet 관련 클래스들도 반드시 public으로 선언하여야 한다.

이외에도 외부에서 멤버필드의 값을 읽거나 값을 변화시키기 위해 사용하는 메소드들도 public 으로 선언되어야 한다.


### protected

protected 는 같은 패키지에 속한 모든 클래스에서 접근이 가능하도록 허용하며 패키지 밖에서도 이 패키지의 클래스를 상속한 하위클래스의 멤버로의 접근이 가능하다.

즉, 패키지 밖에서 이 패키지의 클래스를 상속하여 접근하는 것을 허용하는 것으로서, 클래스 자체에는 사용할 수 없고 멤버 (변수와 메소드)에만 사용할 수 있다.

만일 어떤 프로그램 그룹을 별도로 관리하고자 하는 때에는 패키지를 명시하는 것이 필요하며 이때에는 패키지에 명시된 디렉토리에 따로 파일들을 모을 수 있다.

이때에는 컴파일 시 -d 옵션을 주어야 한다.


### friendly (아무 것도 안 쓴 경우)

접근 지시자를 명시하지 않고 생략한 경우, 즉 디폴트 상태를 friendly 라고 하며, 같은 패키지 내에서의 접근만을 허용한다. (참고로, friendly는 자바 키워드는 아니므로 friendly 라고 쓰는 것은 안된다.)

대부분의 경우 같은 디렉토리내에 있는 자바 소스들은 같은 패키지에 속하는 것으로 컴파일러는 인식한다.

앞에서 설명한 protected와 다른 점으로는 friendly의 경우에는 패키지의 외부에서 패키지 내의 어떤 클래스를 상속받는 경우에도 이 클래스를 패키지 외부에서는 접근할 수 없다는 것이다.

따 라서, protected 보다 접근 허용범위가 좁다고 할 수 있다.

### private

private 는 해당 클래스의 인스턴스에서만 사용할 수 있는 것으로 접근 허용범위가 가장 좁다고 할 수 있다. 또한, 클래스의 하위클래스에서는 상위클래스의 private 멤버를 엑세스할 수 없으므로 유의해야 한다. 

한편, 뒤에서 설명되는 오버라이드(Override)에 자바에서는 허용범위가 좁아지는 private한 방향으로의 오버라이드는 허용하지 않는다.


## 배열

배열(array)이란 연관된 데이터를 모아서 통으로 관리하기 위해서 사용하는 데이터 타입이다. 변수가 하나의 데이터를 저장하기 위한 것이라면 배열은 여러 개의 데이터를 하나의 변수에 저장하기 위한 것이라고 할 수 있다.


```java
	int arr[] = new int[10];
		int arr2[] = {1,2,3,4,5};
		
		for(int a1 : arr){
			System.out.println(a);
		}
		
		for(int a2 : arr2){
			System.out.println(a2);
		}
```



## 생성자

어떤 일을 시작하기 전에 준비를 하게 되는데 이것을 다른 말로 초기화라고 한다. 객체 지향 프로그래밍도 초기화에 해당하는 기능이 제공되는데 이것을 생성자(constructor)라고 한다. 즉 객체를 생성할 때 항상 실행되며, 맨 처음 실행되는 메소드이다.


```java
Calculator c1 = new Calculator(); // 생성자가 호출됨. 

c1.setOprands(10, 20);

c1.sum();

c1.avg();
```

```java
public Calculator(int left, int right) {

this.left = left;

this.right = right;

}
```

### 생성자의 특징

1. 반환값이 없는 메소드는 생성자가 유일하다. 

	생성자는 인스턴스를 생성해주는 역할을 하는 특수한 메소드라고 할 수 있다. 반환 값이 없기 때문에 return도 사용하지 않고, 반환 값을 메소드 정의에 포함 시키지도 않는다.


2. 생성자의 이름은 클래스의 이름과 동일하다.

	자바에서 클래스의 이름과 동일한 메소드는 생성자로 사용하기로 약속되어 있다.

3. 생성자는 매개변수에 따라서 여러 개를 만들 수 있다

	이중에 필요에 따라 객체를 생성시에 선택할 수 있다.
	
	

## 컬렉션

전통적으로 프로그래밍에서 많은 양의 자료(데이터)처리를 위해서는 배열을 이용한다.
	그러나 이 배열은 불편한 점이 2가지가 있다.

	1. 배열에 담는 자료형은 동일해야 한다. 밑에 문장처럼 배열에 한가지 자료형밖에 담을 수 있다.
	한가지뿐 아니라 다른 자료형도 함께 넣고 싶지만 그냥 배열에서는 힘든 부분이다.
	int []arr = new int[100];

	2. 배열은 데이터의 크기를 알 수 없는 경우에는 부적합하다.
	데이터의 크기가 미리 안정해진 경우, 파악하기 어려운 경우는 배열에서 힘들다.
	기준을 많이 잡아놓고 다 사용하지 않는다면 메모리를 차지하고만 있고,
	기준을 낮게 잡아놓으면 기준치초과시 다시 만들어야하는 불편함이 있다.
	String []name = new String[1000]


이런 단점을 보완하기위해서 컬렉션 프레임워크가 만들어짐

### 컬렉션 종류
1. List
	- ArrayList  
	
		```java
					ArrayList array =  new ArrayList();
		```
2. Map
	- HashMap
	
		```java
				HashMap<String,String> map = new  HashMap<>();
				map.put("key1", "이순신");
				map.put("key2", "홍길동");
		```

3. Set

		```java
			HashSet<String> set = new HashSet<String>();
 
   			set.add("1");
    		set.add("2");
    		set.add("3");
    		set.add("4");
    		set.add("5");
 
    		System.out.println(set);

		```


	특징: 순서가 없고, 중복을 허용하지 않음 
	
	장점: 빠른 속도 
	
	단점: 단순 집합의 개념으로 정렬하려면 별도의 처리가 필요하다. 



## 제네릭

컬렉션을 사용할때 타입을 지정하기 위해서 사용
**< >** 를 사용하여 특정 
```java
ArrayList<Integer> array =  new ArrayList<>();
```