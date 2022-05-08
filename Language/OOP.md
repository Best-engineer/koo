## 1. 목적

OOP(Object-oriented programming)란 무엇인가? 자바스크립트 기준으로 살펴본다.

---

## 2. 내용

객체지향 프로그래밍은 사람이 세계를 보고 이해하는 것과 비슷하다.
-> 코드를 추상화하여 직관적으로 생각할 수 있다.
-> Java, C#에서는 철저하게 OOP를 적용했다.  
OOP는 데이터와 기능을 한곳에 묶어서 처리한다.
-> 속성(Property)과 메서드가 하나의 객체라는 개념에 포함된다.
-> 자바스크립트에서는 클래스(Class)라는 이름으로 부른다.  
-> OOP는 하나의 모델이 되는 청사진을 만들고, 그 청사진을 바탕으로 한 객체를 만드는 프로그래밍 패턴이다.

### 2.1 클래스와 인스턴스

## ![OOP](Images/OOP.png)

## ![Class](Images/class.png)

## ![Instance](Images/instance.png)

- 하나의 모델이 되는 청사진 -> class
- 그 청사진을 바탕으로 만들어지는 객체 -> instance
- ES5에서는 function함수형으로 class를 정의했지만, ES6에서는 class라는 키워드로 정의할 수 있다.

```js
function Car(name, color) {}

class Car {
  constructor(name, color) {}
}
```

- **Attribute(속성) 정의하기**  
  this를 사용해서 인스턴스 객체를 생성 한다. constructor에서 받아온 parameter에 새로운 값을 부여한다.

```js
class Car {
  constructor(name, color) {
    this.name = 'avante';
    this.color = 'red';
  }
}
```

- **Method 정의하기**  
  ES5에서는 prototype이라는 키워드를 이용해서 메소드를 정의 했다.  
  ES6부터는 prototype 없이도 메소드 정의가 가능해졌다.

```js
function Car(name, color) {
  Car.prototype.refuel = function () {};
}

class Car{
    constructor(name, color) {
        refuel(){}
        }
    }
}

// 인스턴스 생성
let avante = new Car('avante', 'red');
avante.color;
avante.refuel();
```

### 2.2 OOP 특징

- 프로그램 설계 철학 중 하나다 -> 정답이 아니다.
- 모든 것은 객체로 그룹화된다. -> 데이터와(속성) 기능(메소드)가 함께 있다.
- 4가지 주요 개념을 통해서 재사용성을 얻을 수 있다.
