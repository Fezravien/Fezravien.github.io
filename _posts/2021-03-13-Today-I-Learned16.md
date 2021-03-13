---
layout: post
title: Today I Learned 📚
tags:
  - TIL
  - yagom-ios-camp-2nd
  - ios
  - stackview
hero: https://source.unsplash.com/collection/11663747/
overlay: orange
published: true

---

{: .lead}
<!–-break-–>

# Today I Learned 🔥

## 2021.03.13 (토) 🗓

### 학습내용 📝

#### UIStackView

StackView 란 Auto Layout을 이용해 열 또는 행에 View들의 묶음을 배치할 수 있는 간소화된 인터페이스이다.

- Auto Layout ?

  - 디바이스의 방향, 스크린 사이즈, 혹은 일어날 어떠한 변화에 맞춰서 상대적으로 공간에 UI를 배치하는 기능

  <img src="/Users/yjaewoongnaver.com/Desktop/스크린샷 2021-03-13 오전 1.13.19.png" alt="스크린샷 2021-03-13 오전 1.13.19" style="zoom:25%;" />  

   <img src="/Users/yjaewoongnaver.com/Desktop/스크린샷 2021-03-13 오전 1.10.26.png" alt="스크린샷 2021-03-13 오전 1.10.26" style="zoom:25%;" /> 

  > 조금,, 이상해지긴 하네요 ㅠㅠ

- **View 에 각각 배치해서 Auto Layout를 맞출 수 있지만?**

  - StackView를 사용하면 쉽게 말해 거의 자동으로 맞출 수 있다.

    > 처음에 직접 View에 각각 올려서 맞춰보려고 하다가 화가났다 !

  - View에 각각 배치하는 것과 StackView에 넣어서 배치하는 것을 구분하는 기준

    - StackView에 들어가는 View가 런타임 중에 동적으로 수정되는 경우에 기존 View들의 Layout이 변경되느냐에 따라 나눌 수 있다.

- **Auto Layoutd은 어떤 방식으로 적용?**

  - StackView는 "Arranged Subviews" 프로퍼티에 들어있는 모든 View의 Layout을 관리한다.

    이 View들은 StackView의 arrangedSubviews 배열의 순서에 따라 StackView의 축(`axis`)을 따라 배치된다.

    즉 StackView의 Layout은 축(`axis`), 분배(`distribution`), 정렬방식(`alignment`), 여백(`spacing`)에 따라 배치된다.

    

  - 축(`axis`), 분배(`distribution`), 정렬방식(`alignment`), 여백(`spacing`)

    - 프로퍼티들을 이용해 StackView의 arrangeSubviews 배열에 들어있는 요소에 Layout을 정해준다.

    - StackView의 내부 Content로 StackView를 resize 할 수 있고, 반대로 StackView의 프로퍼티를 조정함으로써 내부 Contents들의 크기를 조절할 수 있다.

      - 사용자는 StackView의 위치와 옵션을 정의해줘야 Contents들의 Layout과 size(옵션)을 조정할 수 있다.

        

<img src="/Users/yjaewoongnaver.com/Downloads/R1280x0.png" alt="R1280x0" style="zoom:50%;" />



- UIStackView.Axis

  StackView는 Stack의 Axis(축)의 각 Edge에 맞춰 Arrangeed View의 첫번째, 마지막 요소를 배치한다. 이는 Horizontal Stack(가로축) 에서는 첫번째 뷴의 왼쪽 Edge가 StackView의 왼쪽 Edge와 동일하게 배치됨을 의미한다.

  Vertical Stack(세로축) 에서는 맨 위쪽 Edge가 StackView의 맨 위, 맨 아래 Edge와 동일하게 배치된다.

  - **가로 세로 버전이라고 생각하면 편하다**

  

- UIStackView.Distrubution

  StackView의 축(Axis)을 따라 Arrange View들을 어떻게 분배할지에 대한 속성

  - UiStackView.Distribution.fillEqually 플래그만 제외하고 모든 Distribution 설정에서, StackView는 축(Axis)의 사이즈를 계산할 때 각 arrangedSubview들의 intrinsicContentSize 프로퍼티를 이용한다.
  - UIStackView.Distribution.fillEqually 플래그는 StackView의 축(Axis)에 따라 StackView를 채우기 위해 모든 Arrange Views들의 사이즈를 동일하게 재조정 한다. 가능하다면, StackView는 모든 Arrange View들을 가장 긴 Size를 가진 View에 맞춰 늘리기를 시도한다.

  

- 정리 !

  - 대부분의 View들은 Content 크기에 맞게 따로 width, height을 지정해주지 않아도 자동으로 auto layout이 적용된다.

    - intrinsicContentSize에서 컨텐츠 크기에 맞는 사이즈를 계산해주기 때문이다

  - StackView에서도 Distribution.fillEqaully 플래그를 제외하고는 ArrangeView들의 intrinsicContentSize 프로퍼티를 이용해 Axis에 따른 StackView의 사이즈를 계산해줍니다.

     

---

##### UIStackView.Axis

- **fill**

  > - StackView의 축(Axis)을 따라 가능한 공간을 모두 채우기 위해 Arrange view들의 사이즈를 재조정하는 플래그.
  >
  > - arrange views들이 StackView의 크기를 초과한다면, 각 뷰의 compression resistance priority에 따라 각 뷰의 크기를 감소시킨다.
  >
  > - arrange views들이 StackView의 크기에 미달이라면, 각 뷰의 hugging priority에 따라 각 뷰를 늘린다.
  >
  > - 모호한 점(ambiguity)가 생긴다면, StackView는 arrangedSubviews 배열의 인덱스에 기초하여 각 뷰들의 크기를 재조정한다.

  

  - compression resistance priority

    - 최소 크기에 대한 저항
    - compression(짜부) 에 대한 resistance(저항)
    - **숫자가 클수록 안작아질거야! 가 강해짐**

  - hugging priority

    - 최대 크기에 대한 저항
    - **숫자가 클수록 안늘어날꺼야! 가 강해짐**

    

  - shrink 해야할 때는 각 view들의 compression resistance priority를 비교해 제일 낮은 뷰 부터 크기를 감소시키고, stretch 해야할 때는 각 view들의 hugging priority를 비교해 제일 낮은 뷰 부터 크기를 증가시킵니다.

    

- **fillEqually**

  > StackView의 Axis(축)을 따라서 가능한 공간을 채우기위해 ArrangedSubView들을 리사이징 합니다. 뷰들은 StacKView의 축을 따라 모두 같은 사이즈를 갖기위해 재조정됩니다.

  StackView의 축(Axis)을 따라 모두 같은 크기로 분배되도록 하는 옵션 

  <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2.png" alt="R1280x0-2" style="zoom:60%;" />

  

- **fillPropertionally**

  > StackView는 축(Axis)에 따라 가능한 공간을 모두 채우기위해 arrangedViews들을 리사이징한다. 뷰들은 그들의 intrinsic content size에 기초하여 비례적으로 사이즈를 재조정한다.

  StackView를 채우고, 남은 공간이 생긴다면 intrinsic content size 의 비율에 맞게 공간을 분배하여 resize 된다.

  <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.png" alt="R1280x0-2-2" style="zoom:60%;" />

  

- **equalSpacing**

  > - StackView의 Axis(축)을 따라 가능한 공간을 채우기 위해 ArrangedSubview들의 위치를 재조정한다.
  > - View들이 StackView를 채우기에 부족하다면, StackView는 뷰들 사이의 공간을 균일하도록 재배치 한다.
  > - View들이 StackView를 초과한다면, 뷰들의 compression resistance priority 에 따라 뷰의 사이즈를 감소시킨다.
  > - 모호함이 있다면, StackView는 arrangedsSubViews 배열의 인덱스에 따라 뷰들을 감소시킨다.

  StackView 내부의 View들 사이의 공간을 균등하게 배치하는 옵션이다.

  

<img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.1.png" alt="R1280x0-2-2.1" style="zoom:60%;" />



- **equalCentering**

  > - StackView의 축(Axis)에 따라 각 View들의 center - center간 거리를 동일하게 View의 위치를 재조정한다.
  > - StackView의 spacing 프로퍼티의 값만큼의 거리는 유지해야 한다.
  > - View 들이 StackView를 초과한다면, spacing 프로퍼티에 정의된 최소 거리만큼을 채울 때 까지 간격을 좁힌다.
  >   - 그래도 초과한다면, 각 뷰의 compression resistance priority에 의거해서 View들을 감소시킨다.
  >   - 만일 더 모호함이 있다면, StackView는 arrangedSubView 배열의 인덱스에 따라 뷰들을 감소시킨다.

  각 뷰의 center - center간 길이를 동일하게 맞추는 옵션이다.

  

  

  

  

  ##### UIStackView.Alignment

  >  StackView의 Axis(축)에 수직인 뷰들의 레이아웃을 정하는 Flag

  StackView가 어떤식으로 하위 뷰들을 정렬할 것인지에 대한 플래그이다.

  

  - **fill**

    > StackVIew의 축(Axis)과 수직인 방향으로 가능한 공간을 채우기위해 View들의 사이즈를 재조정 한다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.2.png" alt="R1280x0-2-2.2" style="zoom:60%;" />

    Axis가 Horizontal인 경우, 아래 위의 공간을 fill 하기 위해 늘리고,

    Axis가 Vertical인 경우, 좌우 공간을 fill 하기 위해 늘리는 플래그입니다.

    

  - **leading**

    

  <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.3.png" alt="R1280x0-2-2.3" style="zoom:60%;" />

  > - Vertical StackView에서 View들의 leading Edge와 StackView의 leading Edge에 맞춰 정렬한다.
  > - Horizontal StackView에서 Top 플래그와 동일한다.

  

  - **top**

    > 가로 축(Horizontal) StackVIew에서 View들의 Top Edge와 StackView의 Top Edge에 맞춰 정렬합니다.
    > 세로 축(Vertical) StackView에서 leading 플래그와 동일합니다.

    

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.4.png" alt="R1280x0-2-2.4" style="zoom:60%;" />

    

  - **firstBaseline**

    > - View들의 first baseline에 맞춰 StackView가 View들을 정렬하는 것을 말한다.
    > - 이 정렬은 오직 Horizontal StackView에서만 유효하다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.5.png" alt="R1280x0-2-2.5" style="zoom:60%;" />

    

    

    

  - **trailing**

    > - Vertical Stack의 Trailing Edge와 뷰들의 Trailing Edge를 맞춰 정렬하는 플래그이다.
    > - Horizontal Stack의 Bottom 정렬과 동일합니다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.6.png" alt="R1280x0-2-2.6" style="zoom:60%;" />

    

  - **center**

    > StackView가 축을 따라서 View들의 center를 StackView의 Center에 맞춰 정렬하는 것을 말한다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-3-2.8.png" alt="R1280x0-3-2.8" style="zoom:60%;" />

    

  - trailing

    > - Vertical Stack의 Trailing Edge와 뷰들의 Trailing Edge를 맞춰 정렬하는 플래그이다.
    > - Horizontal Stack의 Bottom 정렬과 동일하다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.6.png" alt="R1280x0-2-2.6" style="zoom:60%;" />

    

  - bottom

    > - 가로 축(Horizontal) Stack의 Bottom Edge와 뷰들의 Bottom Edge를 맞춰 정렬하는 플래그이다.
    > - 세로 축(Vertical) Stack의 Trailing 정렬과 동일하다.

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.7.png" alt="R1280x0-2-2.7" style="zoom:60%;" />

    

    

  - **lastBaseline**

    > - StackView가 View들의 last baseline에 맞춰 View들을 정렬하는 플래그이다.
    > - 이 정렬은 오직 가로 축(Horizontal) StackView에서만 유효하다

    <img src="/Users/yjaewoongnaver.com/Desktop/R1280x0-2-2.8.png" alt="R1280x0-2-2.8" style="zoom:60%;" />

    

  



### 문제점 / 고민한 점 🤦🏼

- 앱을 만들다 보니 [Step 1] 에서 과일 저장소에 적용한 싱글톤이 뭔가 위치가 어색함을 느끼게 되었다.



---

### 해결방법 🙋🏼

- [Step 1] 에서 과일 저장소에 적용한 싱글톤은 JuiceMaker로 옮김 

  - 과일 저장소는 사용자가 접글할 수 없으며 JuiceMaker가 모든 로직을 담당하므로 싱글톤에 더 적합하다고 생각했다.

  ```swift
  class JuiceMaker {
      
      static let shared = JuiceMaker() // 싱글톤 생성
    
      var fruitStorage = FruitStock(initAmount: 10)
      
      private init() {
      }
      
      func make(order: Juices) throws {
      }
      
      func currentFruitStock() -> Storage {
      }
      
      func addFruitStock(fruit kind: Fruits, amount addFruits: Int = 1) throws {
      }
      
      private func consume(fruit kind: Fruits, amount: Int) throws {
      }
      
      private func hasFruitStock(fruit kind: Fruits, amount: Int) throws {
      }
  }
  ```

