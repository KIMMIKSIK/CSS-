
# **Css 혼란스러운 개념 정리**

css를 공부하면서 알게 된 기록할 만한 내용들을 적어보자.

## @  크기 조절 시 %는 자신의 부모요소이다!

## @  **body태그의 높이를 전체창에 꽉 채우고 싶을때**

(html을 100% 먼저 지정해주고 body를 100%지정해주거나) (body를 100vh로 해주면 된다.) html은 부모가 전체 창이기에 100%지정해주면 그냥 꽉채워짐 **단, 이 방법은 만약 높이가 전체창을 넘어가게 된다면 의미가 없다. 왜냐하면 자식이 만약 더 길어진다면 부모크기는 고정되서 따라 오지 못한다.**

이럴때는 부모는 자식을 따라 높이가 길어지게 일반적으로 두고 바탕이 있다면 min-height:100vh로 준다면 초기 배경이 화면에 꽉차고 자식이 길어져도 같이 늘어나게 된다.

## @ b**ackground 헷갈리는 부분**

background-size: cover **가로든 세로든 무조건 화면을 덮어야한다** 높이가 길어지면 자동적으로 배경사진도 커지게 될 것이다.

background-size: contain 사진의 모든 모습이 화면에 나와야한다. 즉 가로든 세로든 더 긴쪽을 기준으로 화면에 맞추게 되고 그에따라 여백이 생길수도 있다.(화면이길어진다고 해서 커지지는 않는다)

참고 : body태그는 div와 비슷하지만 최상단에 위치해 있기 때문에 그 크기 어찌됬든 background를 걸어주면 내가 보고 있는 화면에 전체에 걸쳐 작동하게 된다.

## @ position을 걸지 않으면 z-index를 설정할 수 없다.

## @ flexbox 내부에서는 float사용 불가

flexbox 자세한 내용 참조: [https://studiomeal.com/archives/197](https://studiomeal.com/archives/197)

## @ margin, padding 설정

시계 방향으로 생각하면 이해가 편하다(top - left)

padding or margin  : 10px(top) 20px(right) 30px(bottom) 40px(left)

## @ width와 다른 까다로운 height

css height 를100% 지정하기 위해서는 부모의 높이가 명확하게 지정되어 있어야함,
(min-height이렇게도 안됨)단, width는 position등의 지정으로 크기가 줄었을시 바로 100%로 채우기 가능.

## @ animation vs transition

속성의 값이 변화할때 스르륵 부드럽게 변화하는건 transition, animation은 그냥 animation효과를 주고싶을 때 사용할 수 있어서 훨씬 더 자유로움

transtion : font-size(property) 2500ms(duration) 요소의 변화 전부 주고 싶을땐 property를 all로 줄 수 있음

## @ Typography

![image](https://user-images.githubusercontent.com/98815511/162003309-dee46f9f-3681-4a49-a8bc-66b81c074ad3.png)


- font-size:

px:절대단위
em: (상대단위) 해당 요소에 실제로 적용된 크기가 1em이 된다.<p>태그에 20px
rem: (상대단위) root em을 의미하며 html태그에 적용된 폰트 사이즈를 1rem으로 한다!

- line-height: px과 rem으로 적용할 때는 반드시 적어주고 em은 관례상 생략가능

font-size: 16px;
line-height: 1.5;

line-height를 쓰더라도 텍스트는 무조건 가운데 위치!

- letter-spacing: 글자 좌우 간격 조절(px,em단위 사용)

![image](https://user-images.githubusercontent.com/98815511/162003376-62218f96-f16d-4210-9a43-935fa1d82c12.png)

- font-weight : 글자 두께를 나타내며 무조건 100단위(400이 regular값)

![image](https://user-images.githubusercontent.com/98815511/162003447-d7482105-267d-4b40-aac5-02fa0e78316e.png)

## @ transform : css에서 제공하는 함수들과 함께쓰임 3개만 기억!

***3가지 다** **공통적으로 변화해도 다른 요소들은 원래 그 요소의 크기와 위치를 기억하고 있다.**

- transform : translate(40px,50px) 원하는 방향으로 위치 시키고 싶을 때 사용(x,y축 입력)
**translate를 %로 입력하면 부모 기준이 아니라 자신의 크기 기준 이동함**

![image](https://user-images.githubusercontent.com/98815511/162003555-a0fef254-5f88-4133-b66e-a94fec5544fc.png)

- transform : scale(0.5) 1을 기준으로 크기를 조절할 때 사용 (배율을 적어준다.)
값을 2개를 적으면 각각 width, height로 적용됨.
- transform : rotate(45deg) 회전시킬때 사용하며 (deg)를 입력한다.360deg면 한바퀴 회전

![image](https://user-images.githubusercontent.com/98815511/162003623-98cb0639-8cea-40f8-b352-90707f234736.png)

## @ box-sizing :content-box(기본값)

content-box는 패딩과 테두리를 포함하지 않는 내용물 박스기준으로 크기를 갖게된다.

width: 10px;
height: 10px;
가로10 세로10은 테두리와 패딩의 기준이 아닌 내용물 박스의 기준이다.
이를 위해서 **border-box**를 사용해주면 된다.

![image](https://user-images.githubusercontent.com/98815511/162003702-6d0cd922-1afd-4c83-a15e-b7c59c2c2c70.png)

## @ box - type : block(길막)줄넘김 일어남

display: block은 길막을 먼저 떠올린다. width를 통해 가로를 줄여도 자동으로 마진을 설정하여 자신의 공간을 꽉꽉 채워서 한줄을 모두 차지한다.
모든 margin, padding 크기 조절이 다 가능하다.
(inline은 크기조절 불가 padding,margin은 가로만 가능)
**margin: 0 auto : box의 width를 지정해준뒤 설정하면 가운데 정렬을 할 수 있음.
inline스타일의 경우 text-align:center와 같다고 볼 수 있다.**

## @ box - type : inline(흐름)줄넘김 일어남

내용물이 길어졌을때 부모를 넘어가도 줄넘김이 이루어지지 않는다.
자신의 부모(block)에 **text-align:center를 사용하면 중앙정렬이 가능하다.** 
**크기조절 불가! padding,margin은 가로로만 가능** 인라인의 줄간격의 흐름을 박살내기 때문에 안됨

![image](https://user-images.githubusercontent.com/98815511/162003796-503bff9f-b029-4bc3-958d-168d6f24ec81.png)

## @ box - type : inline block(짬뽕)

inline의 흐름 형태를 갖추고 있지만 block처럼 영역을 잡을 수 있음 크기조절과 상하 margin, ,padding의 조정이 가능하다. 

참고: 대표적으로 img태그가 있는데 나는 display : block을 적용하면 사진이 한칸을 다 차지하기 위해 가로로 길어질 줄 알았다. 하지만 inline block은 기본적으로 자신의 크기를 가지고 있어서 나머지 공간을 마진으로 채우며 block형태가 되었다.

## @ float (영역을 차지하는 block을 가로 배치하게 하는법)

float를 사용하게 되면 부모와 형제들은 그 자식 요소를 집나간 자식처럼 대하게 된다.(무시하게 된다)
* 그래도 부모의 영역을 벗어나지는 못한다.
**float를 사용한 요소는 무조건 block레벨로 바뀌게 된다!!!즉 크기 조절이 가능해진다. 
그런데 길막을 하지 못하는 block이된다. 흐름을 따르는 block이 된다(자신의 내용물만큼만 차지함)**

![image](https://user-images.githubusercontent.com/98815511/162003884-3553950f-3e08-482a-9be4-d8421088bb34.png)

![image](https://user-images.githubusercontent.com/98815511/162003948-4e02c6d9-4e0a-4e51-a9fe-a177d61ae84c.png)

![image](https://user-images.githubusercontent.com/98815511/162004015-d6744972-2f1a-42db-9177-ba546e6cf08c.png)

셋다 모두 float시키면 부모의 height는 0이된다.

![image](https://user-images.githubusercontent.com/98815511/162004100-2527a623-aa8e-42c4-bb1b-9f72cfa78057.png)

**float는 block은 보지 못하지만 그안에 컨텐츠들은 볼 수 있어서 컨텐츠들은 영향을 받게 된다.**

****참고: float는 순서를 유지하기 때문에 실제로 float한 요소가 앞에있는지 뒤에있는지에 따라 자리를 지키고 있을 수도 있고 본인이 내려갈 수도 있다.

ex) <div>안녕하세요<span style=”float:right;”>김</span>입니다.</div>
”김”은 “안녕하세요” 보단 뒤에 있기 때문에 만약 “안녕하세요”가 길어져서 다음줄로 넘어가게 된다면 “김”이 내려가게 된다 하지만 “입니다” 보단 앞에 있기 때문에 “입니다”가 길어져도 본인의 위치를 지키고 있다.

flexbox

![image](https://user-images.githubusercontent.com/98815511/162004166-362e584e-fb01-4b83-aa16-d21e27107e2c.png)

![image](https://user-images.githubusercontent.com/98815511/162004255-fee282f1-c3f3-4cdc-8f2d-3cf840ee7702.png)

**css 다중 선택자로 여러 요소를 동시에 선택해서 적용 할수 있다.**

**1.공백없이 클래스끼리 붙어있는 경우**

**.class1.class2{}**  ex)-.name1.name2

클래스 속성 내에 name1과 name2가 모두 설정된 모든 요소를 선택합니다.

**2.쉼표가 있는 경우입니다.**

element, element, element { style properties }

css **선택자 목록**(,)은 일치하는 모든 요소를 선택합니다.

쉼표로 구분한 목록을 한 줄에 배치할 수 있습니다.

```
h1, h2, h3, h4, h5, h6 { font-family: helvetica; }
```

3. 공백으로 연결해서 사용 하면 하위 개체로 지정합니다

.

.a .b .c

a클래스 내부의 b클래스 내부 c클래스요소에만 스타일 적용합니다.

## @ 마진중첩현상(무조건 border를 기억하라)

## @ 음수 마진

## **@  css의 상속 inherit**
