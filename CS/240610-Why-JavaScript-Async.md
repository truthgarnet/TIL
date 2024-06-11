# 2024-06-10

## ❓ 오늘의 궁금증

많은 언어들이 동기와 블로킹을 사용하는 데 왜? JavaScript는 비동기이면서 논 블로킹을 사용하는 걸까 궁금증이 발생했다.

## Why JavaScript 비동기?

### 비동기

- **사용자 이벤트 처리**: 사용자 인터페이스와 상호작용을 해야 하는 데, 각종 처리를 할 때 UI가 멈춰 사용자 경험이 떨어질 수 있는 문제점이 발생함
- **네트워크 응답 처리**: 서버에 API를 요청했을 때 언제 응답이 올지 모를 때 비동기 처리를 할 수 있다. → 예를 들어보면, 파일을 전송할 때 파일 크기가 커 보내는 데 오랜 시간이 걸릴 경우에 다른 페이지로 이동하지 못하고 기다려야 하는 상황이 발생할 수 있음 ⇒ 그렇기 때문에 비동기를 사용해 파일 전송까지 기다리지 않고 다른 페이지에서 갈 수 있음

싱글 스레드의 한계를 벗어나 여러 요청을 처리할 수 있게 만들었음

굳이 비동기 작업을 택하면서까지 JavaScript는 싱글 스레드를 선택했을까?

자바 스크립트가 왜 싱글 스레드를 선택 했는지에 앞서 스레드가 무엇인지를 알고 있어야 JavaScript가 멀티 스레드가 아닌 싱글 스레드 + 비동기를 채택했는지 알 수 있을 것 같다.

## What is Thread?

- 프로세스가 할당받은 자원을 이용하는 실행의 단위
- 예전에는 실행 흐름이 프로세스였지만, 소프트웨어가 개발함에 있어 복잡한 동시 작업이 필요해져 하나의 프로세스에 더 작은 단위를 만든 게, 스레드다.
- 예를 들어, 크롬에서 사진을 내려받으면서, 노래를 들으면서 웹 서핑을 할 수 있다.
- 스레드가 많을수록 많은 처리를 할 수 있어서 좋아 보이지만, 그렇지도 않다. (트레이드오프 발생)
<br>
#### 멀티 스레드
- 👍: 멀티 스레드는 속도 면에서 빠르다.
- 👍: 에러 발생 시, 동작이 멈추는 싱글 스레드와 달리 새로운 스레드를 생성해 처리한다.
- 👎: 현재 작업 중인 프로세스에서 다른 프로세스를 넘어가기 위해 현 상태를 저장하는 과정, 동기화 작업으로 스레드 생성 시간이 단일 스레드보다 느리다.
- 👎: 또한, 멀티 스레드는 같은 내용(자원)을 접근할 수 있다는 점에 충돌이 날 수 있다. 마치, Git에 같은 브랜치로 같은 부분을 수정해 commit 하는 것과 같다.

#### 싱글 스레드
   - 👍: 하나의 스레드가 작업 완료되어야 다음 작업이 진행되기 때문에,
   - 👍: 한 스레드만 신경 쓰면 되기 때문에, 프로그래밍 난이도가 쉽고, CPU, 메모리를 적게 사용한다. 단, CPU만을 사용하는 작업은 단일 스레드가 더 빠르다.
   - 👎: 에러 처리를 못 하는 경우 멈춘다.
   - 👎: 연산량이 많은 작업을 할 때, 작업이 완료될 때까지 기다려야 한다는 점으로 시간이 무수히 걸릴 수 있는 점이 있다.

## Why JavaScript Single Thread?

다양한 사용자 작업과 서버의 정보를 받는 등 많은 작업을 해야 하는 곳인 JavaScript에서 싱글 스레드로 작업할까에 대한 의문을 가졌다.

앞서 봤던 내용으로 연산량이 많은 작업일 때 작업이 완료되어야만, 다른 작업을 실행할 수 있는데 왜? 굳이 싱글 스레드를 선택했을까? 여러 곳을 찾아봤는데, 예상하기에는 JavaScript가 만들어진 당시에는 개인용 컴퓨터에 멀티 할 때 사용되지 않았기 때문일 수 있고, 적은 자원의 사용, 빠른 개발이 더 중요하다고 생각했기 때문이 아니겠느냐는 추측들이 나오고 있다.