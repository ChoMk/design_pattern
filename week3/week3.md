# Decorator

- 객체의 결합을 통해 기능을 동적으로 유연하게 확장 할 수 있게 해주는 패턴
- Decorator class 에서 component class의 합성 관계를 통해 표현

# 예시

## 이슈

- road display를 수행하는 객체를 만들자
- 다양한 합성 요소가 있는 road display를 road display interface를 통하여 합성하여 개별적으로 구현하자
- 이슈! → 여러개의 작은 합성 요소를 중복하여 구현해야하는 이슈가 있음
- 해당 이슈의 해결을 위하여 decorator 패턴을 이용하자

 

## 해결

- display decorator interface 선언
- display decorator 구현체를 선언할 때 생성자에서 다른 display decorator를 주입 받음
- 주입 받은 display decorator를 수행하고 구현체에서 수행할 display를 수행하자

## → 이를 통하여 중복하여 구현이 필요했던 합성 요소들을 더 작게 분리하여 중복 구현을 회피할 수 있다.

[https://gmlwjd9405.github.io/2018/07/09/decorator-pattern.html](https://gmlwjd9405.github.io/2018/07/09/decorator-pattern.html)

# Proxy

- 구체적으로 인터페이스를 사용하고 실행시킬 클래스에 대한 객체가 들어갈 자리에 대리자 객체를 대신 투입시켜 클라이언트에게 반환 값을 반환하는 방식.
- 흐름제어만 할 뿐 결과값을 조작하거나 변경시키면 안됨.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45548c64-d2ee-4183-925f-f695c23b5c24/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45548c64-d2ee-4183-925f-f695c23b5c24/Untitled.png)

[https://ko.wikipedia.org/wiki/프록시_패턴](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9D%EC%8B%9C_%ED%8C%A8%ED%84%B4)