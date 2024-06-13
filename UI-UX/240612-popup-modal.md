# **❓ 오늘의 궁금증**

## 모달과 팝업 뭐가 다른 것일까?

처음 이해한 과정은 

1. 모달은 부모(기존) 브라우저의 움직임을 막는다.
2. 팝업은 부모 브라우저와 상관이 없는 새 브라우저가 생성한다
3. 부모 브라우저가 기존 페이지에서 벗어나면 받아야 하는 정보를 받을 페이지에서 벗어난다.
4. 그렇다면 꼭 정보를 받아야 하는 팝업창의 경우는 부모 브라우저를 강제하는 모달을 사용하면 된다!
5. 그래서 모달에는 로그인과 주소 검색과 같은 기능을 넣으면 되는 구나

라고 생각했다. 나는 군더더기 없는 이해인 듯 보였다. 하지만 이는 잘못된 이해 방식이었다. 개발자가 원하는 프로세스대로 진행되는 건 모달만이 아니다. 부모 브라우저를 강제하건 강제를 하지 않건 팝업도 결국 데이터를 넣은 프로세스의 다음 프로세스가 제대로 진행되지 않기 때문에, 똑같다고 볼 수 있다.

### 팝업

1. 팝업은 새로운 브라우저를 띄우는 행위이다. 즉, 메모리를 추가로 사용한다. 
2. 요즘 브라우저는 팝업 차단 기능을 제공하고 있다. 팝업이 씹히는 경우가 발생할 수 있다.
3. 1에서 메모리를 추가로 사용을 하지만, 다시 생각하면 세션을 따로 관리할 수 있다는 장점이 있다.
4. 타사 서비스 연동을 할 때, 별도의 인증 창을 띄우는 팝업을 사용하는 경우가 많다.
5. 사용자가 의도하지 않았을 때 많이 쓰임 (광고) ⇒ 모달과 반대로 부모 브라우저의 상호작용을 막지 않기 때문에, 사용자 경험을 모달보다는 헤치지 않는다.

### 모달

1. 팝업과 다르게, 부모 브라우저의 상호작용(페이지 이동)을 막는다. 
2. 부모 브라우저의 일부이기 때문에 팝업 차단 기능이 적용되지 않다.
3. 사용자의 프로세스에 의해 발생함