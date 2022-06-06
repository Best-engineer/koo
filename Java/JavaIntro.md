## 1. JAVA 동작 원리

로컬 컴퓨터에 JAVA를 실행하기 위해 JDK(Java Development Kit) 설치 -> JVM(Java Virtual Machine)도 함께 설치 됨 ->
Eclipse에서 소스코드를 작성(.java)하면 -> 컴퓨터가 읽을 수 있도록 Compile이 되어야 하는데 -> Eclipse에서는 자동으로 .class파일이 만들어짐 ->
그리고 Run 버튼을 통해 "이거 실행해"라고 하면 -> JVM이 .class 확장자를 읽어서 -> 컴퓨터를 동작 시키게 함.

## 2. 문자열

- Double Quotation Marks(""): String -> 문자열
- Single Quotation Marks(''): Character -> 문자
- \n: 엔터키
- 문자열 안에 Quotation Marks: "Hello \"World\""(백슬래시 사용 )

## 3. 변수 타입

- 자바 언어는 왜 변수 타입을 적어줄까?

  - 타입을 적어줌으로써 변수의 값이 어떤 타입인지 명확하게 알 수 있다.
  - 그러나 매번 변수 앞에 타입을 적어줘야하는 불편함이 있다.

  ## 4. Casting(데이터 타입 변환)

  - 변수에 값이 정수인 경우 -> double로 타입을 선언 하면 -> 자동으로 1.0 실수로 변환해줌
  - 그러나, 실수 1.1을 정수 int로 선언하면 Error -> 잃어버리는 수 0.1이 존재하기 때문에
  - 하지만, 강제할 수 있음 -> 코드에 변환될 타입을 명시 ->

  ```java
    int e = (int) 1.1; // 1로 변환
    double b = (double) 1; // 1.0로 변환
    double c = 1; // 1.0으로 자동 변환(잃는 수가 X)
  ```

- int를 string으로 변환, type 확인하는 메소드

```java
    String f = Integer.toString(1);
    System.out.println(f); // 숫자가 아니라 String이다.
    System.out pringln(f.getClass()); // 출력 -> class java.lang.String
```

## 5.코드 Import 해서 사용하기

- 디렉토리 드래그앤 드랍으로 현재 디렉토리로 복사
- import로 경로 설정 or 파일명 입력시 자동 검색
- new 생성자를 통해 인스턴스 생성하여 사용

```java
  import org.opentutorials.iot.Elevator;
  import org.opentutorials.iot.Lighting;
  import org.opentutorials.iot.Security;

  public class OkJavaGoinHome {

  	public static void main(String[] args) {
  		String id = "JAVA APT 507";
  		// Elevator call
  		Elevator myElevator = new Elevator(id); // Elevator라는 데이터 타입 -> new Elevator("JAVA APT 507")은 Elevator 데이터 타입
  		myElevator.callForDown(1);

  		// Security off
  		Security mySecurity = new Security(id);
  		mySecurity.getExistPeopleNumber();

  		// Light on
  		Lighting hallLamp = new Lighting(id+" / Hall Lamp");
  		hallLamp.on();
  		Lighting floorLamp = new Lighting(id+" / Hall Lamp");
  		floorLamp.off();
  	}
  }
```

## 6. eclipse Debugger

- Breaking Pointer를 사용해서 디버깅 실행
- 화살표시 step over, step into 를 사용

## 7. User 입력에 따라 동작하는 범용적인 코드 예시

- 구글에 java popup input text 로 검색
- showInputDialog을 사용하여 만들 수 있음
- showInputDialog 메소드 import

public class OkJavaGoinHomeInput {

```java
  import javax.swing.JOptionPane;
	public static void main(String[] args) {
		String id = JOptionPane.showInputDialog("Enter a ID");
		// 유저가 입력한 값에 따라서 다른 동작을 하는 범용적으로 사용할 수 있는 코드가 된다.
		String bright = JOptionPane.showInputDialog("Enter a Bright level");

		DimmingLights moodLamp = new DimmingLights(id+" moodLamp");
		moodLamp.setBright(Double.parseDouble(bright));
		moodLamp.on();
	}
}
```

## 자바 환경 변수 추가 방법

- 우분투 터미널: echo ~/.bash_profile -> export PATH="자바경로"

## 자바를 터미널에서 컴파일 하는 방법(class파일이 생김)

- 명령어:javac 파일이름.java
- 파일이름.class파일이 생김

## 라이브러리를 컴파일 하는 방법 - javac 명령어 실행 시 class 경로 오류 시(Import 파일 경로가 변경 되었을 경우)

- 경로를 설정해주는 방법
- javac -cp ".:lib:(다른경로):(다른경로):등등" Okjava.java
- .: 현재 디렉토리에서 찾아봐~
- lib: 디렉토리에서 찾아봐~
- 윈도우에서는 세미콜론(;)을 사용할 것, 리눅스나 맥에서는 콜론(:)

## 라이브러리를 실행하는 방법 - 경로 오류 시

- java OkGoingHome 실행시 오류 화면
  ![경로오류](images/%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%20%EA%B2%BD%EB%A1%9C%EC%98%A4%EB%A5%98.png)
- 경로 설정 해주기: java -cp ".:lib" Okjava
- .:lib 의미: 현재 디렉토리에서 class 파일 찾아서 main 파일으르 실행하고 Elevator코드가 있으면 lib디렉토리로 가서 Elevator class 파일을 읽어서 실행 시켜라!!

## Class, Package, variable, method

- Class: 변수와 메소드들을 합쳐놓은 것
- Package: 여러 Class 의 모음
  ![패키지,클라](images/%ED%8C%A8%ED%82%A4%EC%A7%80%2C%ED%81%B4%EB%9D%BC%EC%8A%A4.png)

## instance

- 인스턴스는 무엇인가? 클래스틑 복재한 것.
- 인스턴스를 왜 사용하는가? 일회용 사용이 아니라, 여러개 작업들을 사용하기 위해서는 인스턴스를 만들어서 사용하는것이 효율적이다.
  하나의 클래스를 사용하기 보다는 new를 붙여서 각각의 다른 상태를 가지고 있는 인스턴스를 만들어서 사용하는 것이 효율적이다.
- Method로 기본 기능을 만들고 -> Class로 비슷한 Method와 변수를 그룹핑해서 수납하고 -> 그 Class를 복제해서 또다른 구조를 만들어 사용한다.

```java
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.PrintWriter;

public class InstanceApp {

	public static void main(String[] args) throws IOException {

		PrintWriter p1 = new PrintWriter("result1.txt");
		p1.write("Hello 1");
		p1.close();

		PrintWriter p2 = new PrintWriter("result2.txt");
		p2.write("Hello 2");
		p2.close();
	}
}
```

- Constructor 가 없으면(ex)Math) 일회용이다.
- Class를 만든 사람이 그 Class를 인스턴스로 만들어 사용하길 원한다면 instructor가 있다.
- Constructor는? new 뒤에 있는 것 ex) new PrintWriter("result1.txt");
- new를 붙이면 복제가 되고 변수 앞에다가 타입적어준다.

```java
class Accounting{
    public double valueOfSupply;
    public double vatRate;
    public double expenseRate;
    public void print() {
        System.out.println("Value of supply : " + valueOfSupply);
        System.out.println("VAT : " + getVAT());
        System.out.println("Total : " + getTotal());
        System.out.println("Expense : " + getExpense());
        System.out.println("Income : " + getIncome());
        System.out.println("Dividend 1 : " + getDiviend1());
        System.out.println("Dividend 2 : " + getDiviend2());
        System.out.println("Dividend 3 : " + getDiviend3());
    }

    public double getDiviend1() {
        return getIncome() * 0.5;
    }
    public double getDiviend2() {
        return getIncome() * 0.3;
    }
    public double getDiviend3() {
        return getIncome() * 0.2;
    }

    public double getIncome() {
        return valueOfSupply - getExpense();
    }

    public double getExpense() {
        return valueOfSupply * expenseRate;
    }

    public double getTotal() {
        return valueOfSupply + getVAT();
    }

    public double getVAT() {
        return valueOfSupply * vatRate;
    }
}
public class AccountingClassApp {

    public static void main(String[] args) {
        // instance
        Accounting a1 = new Accounting();
        a1.valueOfSupply = 10000.0;
        a1.vatRate = 0.1;
        a1.expenseRate = 0.3;
        a1.print();

        Accounting a2 = new Accounting();
        a2.valueOfSupply = 20000.0;
        a2.vatRate = 0.05;
        a2.expenseRate = 0.2;
        a2.print();

        a1.print();
    }
}
```

## inheritance

- 상속 관계도
  ![상속](images/%EC%83%81%EC%86%8D.png)
- PrintWriter 가 Writer를 상속받고 Writer는 Object 를 상속 받는다.
- 상속이란? 상위 클라스 에서 가지고 있는 메소드를 하위 클라스에서 가져와서 사용하는 것을 말한다.
- 만약 상위 클라스 에서 가지고 있는 메소드가 마음에 들지 않을 경우 override하여 덮어쓰기 하고, 현재 class에서 메소드를 찾아서 사용한다.
- java 상속 꼭대기에는 Object 클래스가 있고, Object가 가지고 있는 메소드들은 java의 모든 클래스에서 사용 가능하다.
- 상속의 장점: 부모 클래스의 메소드를 그대로 가져와서 사용 가능함 -> 중복 제거, 상위 클라스 메소드를 가져와서 내마음대로 수정도 가능

## String to double

- Double.parseDouble(args[0])
- ex) double valuOfSupply = Double.parseDouble(args[0]);

## Array

- 배열 만드는 방법
  - 타입 + 필드(변수) = new 타입[길이];
  - ex) Double dividedRates = new Double[5];

## Method

- 메소드란: 서로 연관된 코드를 그룹핑해서 이름을 붙인 정리정돈의 상자다
- 왜사용하는가? 필요한 기능이 있을 경우 일일이 코드를 쓰는게 아니라, 메소드로 따로 구현해 놓고 메소드명만으로 출해서 쓸 수 있다. -> 코드를 간결하게 작성 가능하다.(같은기능을 가진 코드가 1억개가 있다면?)
- 매소드 만드는법: 공식 드래그 -> 마우스 오른쪽버튼 -> Refactor -> Extract Method
- 전역변수 선언 방법: 변수 드래그 -> 마우스 오른쪽버튼 -> Refactor -> Convert Local Variable to Field -> Field name -> Access Modifier(public) -> ok

## Class = Object

- Class란: 서로 연관된 변수와 메소드를 그룹핑해서 이름을 붙인 것이다. -> 정리정돈의 상자
- 클래스를 왜 사용하는가?
  - 여러 종류의 변수와 메소드들이 혼재되어 있어도 -> '클래스소속'을 분명히 밝힘으로써 소속관계를 명확하게 할 수 있음 -> 다른 코드들과 뒤섞이거나 같은 이름의 메소드들이 공존할 수 있음 -> 객체지향
  - 구현된 변수 메소드들을 메인 스트림에 다 적어줄 필요 없이 -> 클래스로 따로 만들어놓고 필요할 때마다 호출해서 쓸 수 있음,

```java
class Accounting{
    public static double valueOfSupply;
    public static double vatRate;
    public static double expenseRate;
    public static void print() {
        System.out.println("Value of supply : " + valueOfSupply);
        System.out.println("VAT : " + getVAT());
        System.out.println("Total : " + getTotal());
        System.out.println("Expense : " + getExpense());
        System.out.println("Income : " + getIncome());
        System.out.println("Dividend 1 : " + getDiviend1());
        System.out.println("Dividend 2 : " + getDiviend2());
        System.out.println("Dividend 3 : " + getDiviend3());
    }

    public static double getDiviend1() {
        return getIncome() * 0.5;
    }
    public static double getDiviend2() {
        return getIncome() * 0.3;
    }
    public static double getDiviend3() {
        return getIncome() * 0.2;
    }

    public static double getIncome() {
        return valueOfSupply - getExpense();
    }

    public static double getExpense() {
        return valueOfSupply * expenseRate;
    }

    public static double getTotal() {
        return valueOfSupply + getVAT();
    }

    public static double getVAT() {
        return valueOfSupply * vatRate;
    }
}
public class AccountingClassApp {

    public static void main(String[] args) {
        Accounting.valueOfSupply = 10000.0;
        Accounting.vatRate = 0.1;
        Accounting.expenseRate = 0.3;
        Accounting.print();
        // anotherVariable = ...;
        // anotherMethod = ...;
    }

}
```
