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
    dounle c = 1; // 1.0으로 자동 변환(잃는 수가 X)
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
