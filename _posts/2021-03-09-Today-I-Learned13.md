# Today I Learned 🔥

## 2021.03.09 (화)

### 학습내용 📝

#### Design Patterns

##### MVC (Model - View - Contraller)

- **Model**

  - 데이터에 관한 로직 담당 (데이터 값 변경 및 관리하기)

- **View**

  - 사용자에게 보여지는 화면 담당 (UI)

- **Controller**

  - Model과 View 연결 (Model 값을 View에 보여주기)

  

`중요` : **View와 Model은 절대로 서로에게 접근하면 안된다!**

- Model과 View는 Controller만 접근할 수 있다.
- 역은 성립하지 않는다 !

### <img src="https://blog.kakaocdn.net/dn/bNcP2j/btqFgwUxESu/H6RpdztQdhEG5dYz5Kkas0/img.png" alt="img" style="zoom:30%;" />

> 출처 : Stanford youtube 



- View에 사용자의 이벤트가 있거나 변화가 생길때 어떻게 처리할까?
  - View의 변화
    - `Delegate`, `DataSource`를 사용하기 
    - `Delegate`의 경우 사용자의 이벤트가 발생했을 때 Controller가 이벤트를 처리해준다. -> **View가 Controller에 접근할 필요없다.**
  - Model의 변화
    - `Notification`, `KVO`를 사용하여 Controller가 감지할 수 있다 -> **Model이 Controller에 접근할 필요가 없다.**



- MVC 장단점
  - 장점 : 생산성이 높다.
  - 단점 : 많은 코드들이 Controller에 집중되어 부담이 커지게 된다. 



- ViewController.swfit (Controller안에 View 존재)

  ```swift
  import UIKit
  
  class ViewController: UIViewController {
  		
    	// View 
    	@IBOutlet weak var message: UILable!
    	@IBOutlet weak var emailTextField: UITextField!
    	@IBoutlet weak var passwdTextField: UITextField!
    	// 여기까지 
    
    	var user: User! // Model 사용하기
   
    	@IBOutlet func didPressLogin(_ sender: UIButton) { // 버튼 이벤트 발생
        	guard let email = emailTextField.text, let passwd = passwdTextField.text else {
            	return 
          }
        	user = User(email: email, passwd: passwd) // User 구조체 초기화 
     			if user.email == "test123@gmail.com" && user.passwd == "123" {
            	message.text = "로그인 성공"
          }
      }
  }
  ```

- User.swift

  ```swift
  // Model
  struct User {
    	var email: String
    	var passwd: String
  }
  ```

- 정리 

  - 예시 코드를 확인해보면 ViewController안에 View가 존재하고 비지니스 로직이 존재한다 
    - 프로젝트가 커지면 ViewController 는 많은 비지니스 로직과 뷰들로 인해 무거워(복잡)진다.



---

### 문제점 / 고민한 점 🤦🏼

- `fork` 받은 `github.io` 블로그 잔디가 안깔려요 ??

  - `fork` 로 받은 저장소에는 잔디가 남지 않는다 ! (이슈로 남길 수는 있음)

  

---

### 해결방법 🙋🏼

- 기존의 `fork` 받은 저장소 파일을 `clone`으로 로컬에 받아서 새로운 원격 저장소를 만들어서 옮긴다.

  - 그러면 잔디가 이제 깔리기 시작한다! 무~ 야 ~ 호 !

  <img src="https://media.tenor.com/images/8d0f9cc888c4ca4b69d79829893c225d/tenor.gif" alt="일본의 무야호 떡집 - 인스티즈(instiz) 인티포털" style="zoom:140%;" />