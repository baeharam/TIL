# 컴포넌트 기반 개발

컴포넌트는 앱의 구성단위이며, 앱을 작성한다는 것은 컴포넌트를 작성한다는 것과 동일한 의미이다. 컴포넌트는 클래스로 나타내어지는데, 일반 클래스와는 다른 특징을 가진다.

클래스의 생명주기를 개발자가 관리하는지, 시스템이 관리하는지에 따라 일반 클래스와 컴포넌트로 나뉜다. 그러나 컴포넌트도 클래스이기 때문에 앱을 만들때 클래스와의 조합이 필요하다. 그렇다면 객체지향 프로그래밍과 무엇이 다른 것일까?

* **독립적인 실행 단위이다.**

A클래스에서 B클래스를 실행하기 위해선 new 연산자를 통해 생성하지만 컴포넌트는 개발자가 직접 생성할 수 없고 **인텐트(Intent)**라는 것을 매개로 하여 결합하지 않은 상태에서 독립적으로 실행해야 한다. 

<img src="https://developer.android.com/images/components/intent-filters@2x.png" height="250px">

* **main 함수 같은 애플리케이션의 진입 지점이 따로 없다.**

예를 들어, SMS 앱에는 목록을 보여주는 컴포넌트와 발송 컴포넌트, 수신 컴포넌트가 있다고 하자. 흔히, 앱을 누르는 시점이 앱이 시작하는 순간이라고 생각하기 쉽지만 앱을 누르지 않아도 **특정 컴포넌트로부터 실행**되어 프로세스가 구동될 수 있다. 당연한 것이, SMS가 전달될 경우 굳이 누르지 않았도 수신 컴포넌트로부터 실행되어 프로세스가 구동되는 것이 이에 속한다. 이렇게 앱의 수행시점은 다양할 수 있기 때문에 main 함수가 없다고 표현한다.

* **애플리케이션 라이브러리 개념이 있다.**

사용자가 SMS 앱을 사용하는데 앱의 컴포넌트 기능 중 하나가 갤러리 앱의 목록을 띄우고 사용자가 선택한 사진을 메시지에 포함하는 기능이라면, SMS 앱에서 갤러리 앱을 실행하면 된다. 그런데 이 때, 두 클래스가 직접 결합하여 실행된다면 자기 앱의 클래스가 아니기 때문에 코드로 실행할 수가 없다. 그러나 컴포넌트 기반이기 때문에 갤러리 앱의 목록 컴포넌트를 라이브러리 형식으로 실행하면 된다. 이런 관점에서 **다른 앱들을 라이브러리로 생각**할 수 있다.

# Android 앱의 구성 요소

Android 앱을 구성하는 필수 컴포넌트에는 4가지가 있으며 각각 다른 목적과 생명주기를 가진다.

* **Activity**

UI가 있는 단일 화면으로, 예를 들어 이메일 앱에선 새 이메일 목록을 표시하는 activity가 있고 이메일을 작성하는 activity가 존재하는 것이다. 여러개의 activity들이 같이 작동하여 UI를 형성하지만 독립적인 개념이다. 따라서 만약 이메일 앱에서 사용자가 사진을 찍어 보내려고 하면 카메라의 독립적인 activity를 실행시켜 작동하게 할 수 있는 것이다.

* **Service**

백그라운드에서 실행되는 컴포넌트로 UI를 제공하지는 않는다. 예를 들어, 사용자가 다른 앱에 있는 동안 백그라운드에서 음악을 재생하는 것이 이에 속한다. 

* **Broadcast receivers**

이벤트를 처리하는 컴포넌트로, 안드로이드의 Intent를 받아서 처리한다. Pub/Sub 형태로 바인딩되며, 특정 intent가 발생하면 이를 subscribe하는 broadcast receiver가 이를 받아서 처리한다. 예를 들어, 화면이 꺼졌다거나 배터리 잔량이 부족하다거나 사진을 캡처했다는 것을 알리는 broadcast가 있다. 상태표시줄 알림을 생성하여 사용자에게 broadcast 이벤트가 발생했다고 알릴 수 있다.

* **Contents provider**

앱의 데이터 집합을 관리하는 개념으로 파일 시스템이나 데이터베이스, 웹 등에 저장할 수 있는 모든 데이터를 관리한다. 다른 앱들은 contents provider가 허용하면 데이터를 읽거나 수정할 수 있다. 예를 들어, Android 시스템은 contents provider에게 연락처 정보를 관리하게 하는데 다른 앱들에게 이 정보에 대한 권한을 허용하면 연락처 정보를 읽거나 수정할 수 있는 것이다.

## 출처

* [조대협님 블로그](http://bcho.tistory.com/1038?category=584380)
* [안드로이드 공식문서](https://developer.android.com/guide/components/fundamentals)
* 깡샘의 안드로이드 프로그래밍