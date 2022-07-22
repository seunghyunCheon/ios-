<h1 align="center">ios-mechanism</h1>

# 뷰 컨트롤러의 생명주기 ♼

## 생명주기의 이해, 필요성
- 뷰 컨트롤러에는 애플이 미리 만들어놓은 생명주기가 있고, 이를 반드시 알아야 하는 것은 아니지만 알고있다면 앱의 디테일한 부분들을 다룰 수 있기 때문에 알고 있는 것이 좋다.
- 화면에 나타나는 view의 생성시점과 사라지는 시점에 따라 데이터를 생성, 저장시키는 로직을 설계할 수 있기 때문에 앱의 기능적인 요소 뿐만아니라 안정성과 같은 비기능적인 부분을 향상시킬 수 있다.    
- 다음 화면에서의 변경사항 업데이트에 대해서(서버에서 데이터를 다시 받아올 떄) 동기화를 시켜줘야하기 때문이다.
<p align="center"> 
<img width="400" alt="image" src="https://user-images.githubusercontent.com/70146658/180388249-b941d45c-cef1-4e6f-abee-b49da28bd735.png">
</p>
<p align="center">
viewController 라이프사이클
</p>

## 각 생명주기 함수들의 의미
### loadView
- ViewController를 구성하는 View에 대한 부분을 메모리에 올리는 작업.
     
### viewDidLoad
- 화면이 보여질 때 처음 실행하는 함수
- ViewController가 스토리보드와 연결이 되었을 때(IBOutlet, IBAction) 실행 -> ⭐️ 뷰가 생성되었을때 한번만 호출
- 앱의 초기화면을 구성할 때 사용

### viewWillAppear
- 실제 스크린에 뷰가 화면에 나타나기 전에 호출
- viewDidLoad와 다르게 화면 흐름이 바뀌었다가 돌아오면 다시 실행됨(viewDidLoad는 딱 한번만)
- 화면에 뷰가 나타나기 전에 설정하는 로직을 설계

###  viewDidAppear
- 스크린의 뷰가 화면에서 나타났을때 호출
- 애니메이션 시작과 같은 부분들을 정의

### viewWillDisappear
- 뷰가 화면에서 사라지기 전에 호출
- 애니메이션 멈춤과 같은 부분들에 사용

### viewDidDisappear
- 스크린에 뷰가 사라진 뒤에 호출
- 메모리에서 없어진 것은 아닌 상태


# 앱의 생명주기 ♼
- 앱 레벨에서의 생명주기이며, 예시로 앱을 사용하면서 전화가 올 때 기존에 사용하던 앱의 데이터는 어떻게 처리해야하는가와 같은 앱 레벨의 특정시점에 대한 부분을 다루는 생명주기.
- 앱의 생명주기는 ios12버전을 기준으로 구조가 바뀐다.
- 이전에는 App Delegate에서 앱의 상태관리와 UI 라이프사이클 둘 다 다뤘지만, scene의 개념이 생기면서 이를 App Delegate와 Scene Delegate 두 개로 분리되었다.

<p align="center">ios 12이전</p>
<p align="center"><img width="714" alt="image" src="https://user-images.githubusercontent.com/70146658/180412218-5d3181f3-b365-4a3f-b3ce-9857e4e1688b.png"></p>

<p align="center">ios 12이후</p>
<p align="center">
<img width="724" alt="image" src="https://user-images.githubusercontent.com/70146658/180412752-f64979f6-005e-418e-b761-282ad261c66d.png"></p>
<p align="center">(해당 사진은 WWDC영상에서 가져왔습니다)</p>

### 바뀐 appDelegate의 역할
- 앱의 데이터 구조를 초기화하고 환경설정을 하는 것.
- 앱 레벨에서의 알림 및 이벤트에 대응하는 것
- 애플 푸쉬 알림 서비스와 같이 실행시 요구되는 모든 서비스를 등록하는것.

### sceneDelegate의 역할
- AppDelegate에서 Scene Session을 통해서 scene에 대한 정보를 업데이트 받는다.
- Scene Session에서는 scene을 요청할 때 scene을 추적하는 session 객체를 생성하고, 그 session 내부에서 고유한 식별자와 해당 scene의 세부사항이 들어있다. 
- 즉 사용중인 앱이 잠시 background-running상태로 이동하거나, 비활성화 상태가 될 때, 비활성화에서 활성화상태로 이동할 때의 시점들을 sceneDelegate에서 처리하는 것이다.
       
       
      
      
#### 참고:
- https://subscription.packtpub.com/book/application-development/9781783550814/6/ch06lvl1sec60/uiviewcontroller-lifecycle-methods
- https://developer.apple.com/documentation/uikit/uiapplicationdelegate
- https://lena-chamna.netlify.app/post/appdelegate_and_scenedelegate/
