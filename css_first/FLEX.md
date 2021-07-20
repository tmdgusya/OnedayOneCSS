# FLEX

요즘 회사에서 **열심히 급하게 웹 싸이트의 디자인을 변경하고 만들어야 하는 일때문에 CSS** 를 만지고 있는데 내가 리액트를 공부를 했지만,
**CSS 는 전혀 기본기가 안되어 있다는 생각이 강하게 들었다.** 그래서 **CSS 를 하루에 한번은 되도록이면 공부해서 올리려고 한다.**
여하튼 오늘 FLEX 를 한이유는 오늘 한 일중에 **4개의 아이콘을 한라인에 적당한 간격으로 배치해야 할 일이 생겼는데, 드림코딩 엘리의 FLEX** 강의가 떠올라 그걸 적용해보았다.

일단 목표는 아래와 같이 네모 네개를 배치하는 것이였다.

![](https://rlogimgcontainer.s3.ap-northeast-2.amazonaws.com/squares.png)

그렇다면 우리의 아이템들이 그냥 div 만 씌워져있는 아래와 같은 상태라고 해보자.

```html
<div class="flex_div">
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
</div>
```

![](https://rlogimgcontainer.s3.ap-northeast-2.amazonaws.com/itemsblock.png)

**나의 목표는 위의 네모를 가로축으로 정렬하면서, 일정한 간격으로 두는것**이였다. 

Flex 는 아이템의 레이아웃을 만들어 주기 위해서 나온 속성으로 **Flex div 는 Flex Container** 가 되고, 안의 **아이템들은 Flex Item 이 된다.** 
이렇게 두개의 속성을 나눠둔 이유는 즉, 두가지에 **Flex 와 관련된 CSS 를 적용할 수 있기 때문이다. 일단 해당 사항은 밑**에서 알아보자.

Flex 는 **기본적으로 Item 을 가로로 배치**해준다. 우리의 아까 아이템에 flex_div 에 **display:flex** 라는 속성만 간단하게 줘보겠다.


![](https://rlogimgcontainer.s3.ap-northeast-2.amazonaws.com/flexd.png)

이제는 갑자기 이렇게 붙어버리고 말았다. 그건 아까는 margin-top 을 주었는데 이제는 margin 이없기에 위처럼 보이는 것이다.
일단은 가독성을 위해 조금의 margin-left: 10px 만 주도록 하겠다.

![](https://rlogimgcontainer.s3.ap-northeast-2.amazonaws.com/flexdma.png)

일단 이렇게 하니 가독성이 좀더 좋아졌다. 하지만 Flex 는 단순히 가로로 배치하기 위한것이아니라, 레이아웃을 쉽게 그리기 위해 나온 속성이므로 세로축이나 역축으로도 정렬이 가능하다.
즉, Flex 에는 축이 존재한다는 뜻이다. 즉 Direction 이라는 속성이 존재한다. 해당 속성의 이름은 flex-dircetion 이다.

![](https://rlogimgcontainer.s3.ap-northeast-2.amazonaws.com/flexdirection.png)

이렇게 축을 정할 수 있는데 나는 **row** 형태로 배치해야 하니, 가만히 두겠다. 왜냐하면 default 가 row 이다.

일단 이렇게 됬으니, 내 가로로 세우겠다는 목적은 성공했고, 이제는 사이 간격조절이 필요하게됬다. 마진은 좋은 옵션은 그렇게 아니라고 생각하기에 **flex 에서 해결할 방법**을 찾아보려고 했다.
그래서 flex 의 정렬옵션에 대해서 찾아봐야 했다. **flex 의 정렬옵션에는 justify-content** 가 있었다.

- flex-start(default) : 아이템들의 direction 의 **시작지점으로 정렬**을 합니다. 즉 우리같은 상황에서는 row 이므로 왼쪽부터 정렬을 하겠죠?

- center(default): 아이템을 **가운데로 정렬**하는 옵션인데 중요하게 생각하셔야되는건, 축의 가운데라는 겁니다!

- space-between: 아이템들 **사이사이에 균일한 간격**을 만들어주는 옵션입니다.

- space-around: 아이템들의 **둘레에 균일한 간격**을 만들어주는 옵션입니다. 이 둘레라는 말이 참애매한데, 아이템을 **사각형으로 보고 이해하는게 정말편하다,** 즉 **사각면 중 축의 해당하는 면 모두에 간격**이 생기게 된다. space-between 은 아이템들 사이에만 생기는 것이다.

- space-evenly: 이건 space-around 와 솔직히 무슨차이인지 잘모르겠네요..

일단 이렇게 5가지 옵션중 내가 사용해볼만한 옵션은 **center 로 모은뒤, margin 에 px, vw 로 일정한 간격으로 두는 것** 혹은, **space-between 정도로 간격을 균일하게 주는것**이 필요해보였다.

여하튼 나는 웹을 만드는데 space-between 과 양쪽끝에 padding 을 주는 방식을 채택했는데, **지금 글을 쓰다보니 느낀건 center 로 모은뒤 margin이 좀더 괜찮았을거란 생각**도 든다.

여하튼 이렇게 가로로는 잘 모았는데, 또 하나의 요구사항이 있었다.

**아 수직축에도 맞게 정렬해주세요..** 라는 요구사항이 나왔고, 이제는 축과 반대대는 방향의 Center 로 모으는 방법을 찾아야 했다. 
이렇게 찾다보니 flex-item 에 속성 중 **align-items** 라는 것을 알게 됬다. 

align-items 에는 네가지 속성이 있는데 속성은 아래와 같다.

- stretch : 이 속성은 진짜 말그대로 수직축에 맞게 쭉늘어난다. 이 옵션은 내가 사용하니 div 를 꽉채워버려서 당연히 선택할 수 없는 옵션이다.

- flex-start : 이 옵션은 아이템을 기본축의 수직축의 시작지점으로 몰아버려서 내가 고를수 없는 옵션이였다.

- flex-end : 이 옵션도 .. 수직축의 끝 지점으로 몰아버려서 내가 고를수 없는 옵션이였다.

- center : center 는 정확히 수직축의 가운데로 설정해주기때문에 내가 고를수 있는 옵션이였다!!! 이제 나의 사각형들은 일정한 간격과 가운데에 놓이게 되었다.

- baseline : 베이스라인은 텍스트 라인을 기준으로 한다고 한다.. 근데 잘 모르겠다.

## 아무말

여하튼 회사에서 적용한 내용을 정리도 할겸, 정리를 해야 머리속에 잘 와닿으므로  앞으로의 프론트엔드 프로젝트에서는 CSS 를 중요하게 적어보려고 한다.
누가 이걸보면 이사람은 프론트 취준생인줄 알겠지만.. 백엔드로 취업을 하다보니 이런 프론트의 기본기에 약하다. 앞으로는 더 열심히 공부해서 CSS 도 잘해지고 싶다


