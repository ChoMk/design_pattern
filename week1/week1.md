# 중재자 패턴 Mediator Pattern

모든 클래스간의 복잡한 로직을 캡슐화하여 하나의 클래스에 위임하여 처리하는 패턴 .→ M:N의 관계에서 M:1의 관계로 복잡도를 떨어뜨려 유지 보수 및 재사용성, 확정성에 유리한 패턴.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/828a6ae5-b70d-4857-9962-087c45c60772/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/828a6ae5-b70d-4857-9962-087c45c60772/Untitled.png)

중재자가 notify한다는 의미로 옵저버 패턴과 매우 유사한데, 옵저버는 구독자가 받기만 하는데 중재자는 서로 통신한다는 것에서 차이가 있다.

[https://ko.wikipedia.org/wiki/중재자_패턴](https://ko.wikipedia.org/wiki/%EC%A4%91%EC%9E%AC%EC%9E%90_%ED%8C%A8%ED%84%B4) ← 코드는 해당 링크로

[https://www.crocus.co.kr/1542](https://www.crocus.co.kr/1542)

## 어디에 사용하면 좋을까?

### 가정

- 뷰페이저로 구성된 페이지가 있다하자.
- 뷰페이져에 그려진 뷰들을 a,b,c라고 가정하자.
- 이때 a에서 x라는 어떤 이벤트가 발생할 때 b,c에서도 x에 대한 이벤트를 처리(뷰의 상태 변화)해야하는 스팩이 있다고 가정하자.

### 구현

### Mediator

- viewpager의 fragment(Command)를 관리하는 리스트
- executeX를 모든 리스트에 대하여 수행

### Fragment

- Command로 확장
- Mediator 주입시에 해당 Command 등록
- executeX 구현체 선언

### 시나리오

- a view → x event가 발생하는 행위 수행 → x 수행 → Mediator에 등록된 모든 Command에 대하여 x Command 수행

# Bridge patter

- 구현으로부터 추상레이어를 분리하여 이 둘이 서로 독립적으로 변화할 수 있도록.
- 구현부에서 추상층을 분리하여 각자 독립적으로 변형이 가능하고 확장이 가능하도록 한다. 즉 기능과 구현에 대해서 두개를 별도의 클래스로 구현을 한다.

### 브릿지 패턴과 어댑터 패턴의 차이

- 어댑터는 결국 어떤 코드에 맞게끔 기존의 코드를 쓰기 위해 사용되고, 브릿지는 확장성을 고려하여 미리 예상하여 bridge class를 구현해 코드 작성시 사용되어진다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3fa98210-fdbf-4ae7-b15f-be36c807db3c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3fa98210-fdbf-4ae7-b15f-be36c807db3c/Untitled.png)

[https://www.crocus.co.kr/1537](https://www.crocus.co.kr/1537)

## 어디에 사용하면 좋을까?

### 가정

- 어떤 피쳐에 의한 공통된 주제(melody라 가정)를 갖는 페이지를 만들었다고 가정하자.
- 해당 멜로디에 대한 다운로드, 쉐어, 구매, 정렬이라는 4가지 카테고리 기능이 있다고 가정하자
- 쉐어 - 인스타, 페북, 카카오, 라인
- 구매 - 7일 구매, 장기구매, 등등
- 다운로드 - 모든 멜로디 다운로드, 선택 다운로드
- 정렬 - 이름 정렬, 발매일 정렬

### 구현

- 4가지 카테고리 기능에 대한 인터페이스 선언
- 기능 인터페이스를 들고 있는 melody 추상 클레스 선언
- melody 추상 클레스를 통한 각각의 melody 구현체 구현
- 단일 기능(인스타 공유, 7일 구매, 등등..)을 각 카테고리에 맞는 인터페이스를 확장하여 구현
- melody구현체를 사용할 때 해당 melody에서 사용할 기능들을 주입
- 해당 melody로 필요한 기능들 수행