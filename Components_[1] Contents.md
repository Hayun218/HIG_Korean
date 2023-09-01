# HIG-Components_Contents

1. [Charts](##Charts (onGoing))

2. [Image Views](##Image views)
3. [Text Views](##Text views)



## Charts (onGoing)

- 데이터를 차트로 정리하여 명확성과 시각적 어필하면서 소통

![Charts](https://docs-assets.developer.apple.com/published/e60ec631128010abf4cf09793552a20a/components-charts-intro@2x.png)

- 효과적인 차트는 데이터셋에서 몇몇개의 정보만 강조함으로써, 사람들이 인사이트를 얻고 결정을 내리도록 도와준다.
- 예를 들어, 사용자가 차트를 사용하는 목적은 아래와 같다:
  - 기상예보를 보고 계획을 짜는 행위
  - 과거 행적과 현 트랜드를 발견하여 주식 추이를 분석
  - 현재 행적과 새로운 목표를 설정하기 위해 피트니스 데이터를 리ㅂ

### Anatomy

![Charts_Anatomy](https://docs-assets.developer.apple.com/published/99ff482fad4dd4768a7280ce055bbe5d/charts-anatomy@2x.png)

### Marks

- 전해주고자 하는 정보에 따라서 마크의 종류를 설정해야 한다.

1. Bar → 다른 카테고리 혹은 뷰에 있는 값들을 비교하는데 용이
   - 시간에 따라 변하는 데이터
   - 하루에 걸은 걸음수와 같이 각각의 값이 합을 나타낼때 표시하기 용이
2. Line → 시간에 따른 변화를 보이는데 용이
3. Point → 별개의 값들을 각각 표기할때 용이
   - outliers and clusters를 확인할 때 편함
   - 포인트 마크의 집합은 두개의 서로 다른 프로퍼티가 어떻게 서로 연관되어 있는지 보여줌

- 차트의 명확성을 더하기 위해서 마크의 종류를 병합하는 방안도 고려하여야 한다.

  - line + point → 시간에 흐름에 따른 데이터에서 각각의 데이터 포인트를 point 마크로 강조하여 표기

    ⇒ 포인트들을 라인으로 표기하면서 전체적인 방향성과 흐름도를 파악할 수 있도록 하며 포인트 마크를 통해 각각의 값에 대한 집중도도 향상

**Developer documentation**

- **Swift Charts**



## Image views

- 투명하거나 불투명한 배경에 하나 (경우에 따라서 이미지들의 애니메이션 효과 전환)을 보여주는 화면

![ImageViews](https://docs-assets.developer.apple.com/published/75a4736b08754bbd37dad68ddd0048b9/components-image-view-intro@2x.png)

- 이미지뷰는 주로 상호작용이 없다.

### Best Practices

- 뷰의 

  주 목적이 단순하게 이미지를 보여주는 것

  일 때 이미지 뷰를 사용한다.

  - 흔치 않은 경우에 이미지가 상호작용적으로 보이기 원할 때, 이미지 뷰에 버튼 역할을 추가하는 것이 아니라 시스템 제공 버튼을 통해 이미지를 보인다.

- 아이콘을 보이고 싶을 때, 이미지뷰보다는 심볼이나 인터페이스 아이콘을 사용하도록 한다. (→ SF Symbols&icons)

### Content

- 여러 형식으로 이미지를 담을 수 있다. → PNG, JPEG, PDF
- 이미지들 위에 텍스트를 오버레이 할 때 주의하라.
  - 텍스트를 오버레이 할 때, 이미지와 텍스트의 가독성을 저하시킬 수 있다. 텍스트 **대조**를 잘 설정하고, **텍스트 쉐도우**나 **백그라운드 레이어**를 더해 텍스트가 잘 보이도록 한다.
- 애니메이션 시퀸스에서 모든 이미지가 동일한 사이즈를 지닐 수 있도록 하라.

### Platform Considerations

- iOS나 iPadOS에는 추가사항 없음

**<Mac OS>**

- 편집가능한 이미지 뷰가 필요할 때, image well을 사용해라
  - image well → 이미지뷰에서 수정가능
- 클릭이 가능한 이미지를 만들 때는 이미지 버튼을 활용해라
  - image button

**<tvOS>**

- 이미지들에 투명도를 추가한 여러 레이어들을 합쳐서 심도를 형성한다
  - Layered images

**<watchOS>**

- 가능하다면 swiftUI를 활용해서 애니메이션을 만들어라
  - 가능하다면, WatchKit을 활용해라 (**WKImageAnimatable**)



## Text views

- 편집가능할 수도 있는 여러 줄, 스타일된 문자 내용을 비치

![TextViews](https://docs-assets.developer.apple.com/published/c626bcee9f9dc28ab4335f7163fd9062/components-text-view-intro@2x.png)

- 내용이 뷰 밖으로 나올 경우 스크롤할 수 있으며, 어떠한 높이든 가능한다.
- Defult: 텍스트 뷰는 leading edge를 지니며, 시스템 라벨 컬러를 사용한다.
- iOS or iPadOS → 텍스트 뷰가 편집가능하다면, 뷰를 클릭시 키보드가 나오도록 되어 있다.

### Best practices

- 길거나 편집가능하거나 특별한 포맷을 지니고 있는 텍스트를 비치할 경우 텍스트 뷰를 사용한다
  - 텍스트를 보여주거나 텍스트 인풋을 받는 대부분의 옵션을 제공하는 Text filelds와 Labels와는 다르다.
  - 작은 양의 텍스트를 보여줄 때는, 편집가능한 텍스트일 때 text field보다 label을 사용하는 것이 간단하다.
- 글자를 읽기 쉽도록 해라
  - 여러개의 폰트, 색상, 배열을 창의적으로 사용할 수 있지만, 가독성을 유지하는 것이 가장 중요하다.
  - 사용자가 텍스트 사이즈를 기기에서 변환할 때 텍스트 형태를 그대로 유지하고 가독성을 유지하기 위해서 Dynamic Type을 적용하는 것이 좋다.
  - accessibility option이 적용가능하도록 하여라 ⇒ 볼드체 등등
- 유용한 텍스트는 선택가능하도록 해라
  - 유용한 정보를 담은 텍스트 뷰 (에러 메시지, 시리얼 번호, IP 주소)는 사람들이 선택하고 복사하여 붙여넣기 할 수 있도록 만들어라

### Platform considerations

- macOS나 watchOS에는 추가사항 X

**<iOS, iPadOS>**

- 적절한 키보드 타입을 보여라
  - 여러 다른 형태의 키도브 타입은 가능하지만, 서로 다른 인풋을 위해서 디자인 되었다.
  - 참고자료: [Onscreen keyboards](https://developer.apple.com/design/human-interface-guidelines/onscreen-keyboards)

**<tvOS>**

- 텍스트뷰를 통해 tvOS에서 텍스트를 비치할 수 있다. 디자인적으로 tvOS에서 텍스트 입력은 최소화 되어 있기에, 편집가능한 텍스트는 [Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields)를 사용한다!

### Resources

**<Related>**

[Labels](https://developer.apple.com/design/human-interface-guidelines/labels)

[Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields)

[Combo boxes](https://developer.apple.com/design/human-interface-guidelines/combo-boxes)

**<Developer documentation>**

[*Text*](<https://developer.apple.com/documentation/SwiftUI/Text>)
[*UITextView*](<https://developer.apple.com/documentation/uikit/uitextview>)
[NSTextView](<https://developer.apple.com/documentation/appkit/nstextview>)