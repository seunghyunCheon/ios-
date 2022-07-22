<h1 align="center">ios-mechanism</h1>

# 뷰 컨트롤러의 생명주기 ♼

## 생명주기의 이해, 필요성
- 뷰 컨트롤러에는 애플이 미리 만들어놓은 생명주기가 있고, 이를 반드시 알아야 하는 것은 아니지만 알고있다면 앱의 디테일한 부분들을 다룰 수 있기 때문에 알고 있는 것이 좋다.
- 화면에 나타나는 view의 생성시점과 사라지는 시점에 따라 데이터를 생성, 저장시키는 로직을 설계할 수 있기 때문에 앱의 기능적인 요소 뿐만아니라 안정성과 같은 비기능적인 부분을 향상시킬 수 있다.     
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


















#### 참고: https://subscription.packtpub.com/book/application-development/9781783550814/6/ch06lvl1sec60/uiviewcontroller-lifecycle-methods
