# HIG-Components_[2] Status

1. [Activity rings](#Activity-rings)
2. [Gauges](#Gauges-(level-indicator-in-macOS))
3. [Progress indicators](#Progress-indicators)
4. [Rating (-ing)](Rating-(-ing))



## Activity rings

- Move, Exercise, Stand 목표를 향한 개인의 데일리 과정을 보여줌

![activity rings](https://docs-assets.developer.apple.com/published/715b90d471efa2d8c388287bc5fe1700/components-activity-ring-intro@2x.png)

### Best practices

- 앱의 목적과 연관있을 때 Activity rings를 보여준다.
  - 헬스나 피트니스와 관련되어 있을 때, 사용자는 Activity rings이 인터페이스에서 보여지길 기대한다.
- Activity rings을 Move, Exercise, Stand 정보를 보여주기 위해서만 활용한다.
  - 다른 목적을 위해 rings을 표기하지 말고, 동시에 위의 세가지를 다른  ring-link 형태로 보이지 마라.
- Activity ring의 색상을 유지해라 → for a consistent experience
- 항상 검은 배경화면 위에 링을 보여라
- Activity ring의 마진을 항상 유지해라
  - 미니멈 마진을 지니고 있다. 둥근 원형 안에서 보여질 때, circular mask를 씌우지 말고 corner radius를 조정해라
- Activity ring을 다른 ring-like elements와 차별성을 두어라.
- ‘활동’ 앱에서 보내는 것과 동일한 정보를 반복하는 알림은 보내지 마라.
  - 시스템에서 보내는 것과 동일한 알람 X
- Activity rings을 장식품으로 사용하지 마라
- Activity rings으로 브랜딩하지 마라
  - 활동 정보를 앱에 보이는 용도이므로 앱 아이콘이나 마켓팅 용품으로 사용 금지!

### Patform considerations

- iPadOS나 watchOS는 추가사항 X
- macOS와 tvOS 지원 X

**<iOS>**

- HKActivityRingView를 통해 지원가능
  - 애플 워치가 페어링 되어 있으면 저절로 변화함
    - 워치 페어링: 링 3개
    - 워치 페어링 X: Move ring 1개



## Gauges (level indicator in macOS)

- 범위 내의 특정 숫자를 표기할 때 활용

![Gauges](https://docs-assets.developer.apple.com/published/f32c347212ea5d73bc63f86d1a866225/components-gauges-intro@2x.png)

- 범위 안에 현재 값을 표시하는 것 뿐만 아니라, 범위 자체에 대해 많은 정보를 담을 수 있다. 예를 들어, 온도에서 최고점과 최저점을 표시할 수 있고, 변화하는 값을 강조하기 위해서 색상으로 나타낼 수 있다.

### Anatomy

- 값의 범위를 나타내기 위해 원형 혹은 선형 gauge에서 현재 값을 위에 맵핑하여 표기한다.
- gauge에서 추가적으로 macOS는 level indicators를 지원한다.

### Best practices

- 현재값, 최고점, 최저점을 간결한 라벨링으로 작성한다.
  - 모든 gauge style이 이를 기록하는 것은 아니지만, VoiceOver가 스크린을 보지 않고도 보이는 라벨을 읽어 사람들을 도와준다.
- gauge의 목적에 맞게 그래디언트로 길을 채우는 것을 고려해라
  - 예시) 온도 게이지에서는 red → blue 색상을 활용해서 hot → cold를 표기

### Platform considerations

- iOS, iPadOS, watchOS 추가고려사항 X
- tvOS 지원 X

**<macOS>**

- 게이지 뿐만 아니라 범위 내에 특정 숫자를 표시하기 위한 

  level indicator

  가 정의되어 있다.

  - capacity, rating, relevance(흔치않음) 을 설계할 수 있다.
    - capacity ⇒ **descrete** or **continuous**

- 큰 범위에서는 continuous 연속 스타일을 활용해라

  - 넓은 범위에서 비연속 capacity는 활용하기 너무 작아진다.

- 범위의 중요한 파트에 대해서 색상을 변경하는 것을 고려해라

  - default는 녹색이지만, 앱의 상황에 따라서 특정 값에 도달하였을 때 색상을 변경하여도 된다. 전체 색상을 변경하거나, tiered level appearance 로 활용하거나!

- Rating indicator → rating style을 통해 사용자가 랭킹을 확인할 수 있다.

- 잘 사용되지 않지만, 연관성 표시를 위해서 shaded horizontal bar를 활용한다. 예를 들어, 검색 결과에서 연관성을 시각화할 수 있다.

### Questions

1. macOS에서만 level indicator가 정의되는것인가?
2. 선형 게이지는 비연속성으로 표기할 수 없는가?



## Progress indicators

- 콘텐츠를 로딩하거나 오래걸리는 작업을 할 때, 사용자가 앱이 진행 중인 상태를 확인하기 위함

![indicators](https://docs-assets.developer.apple.com/published/983ffd361839ffc1360b1542a8205a45/components-progress-indicators-intro@2x.png)

- some progress indicators는 완료될 때까지 소요시간을 표기하여 준다. all은 일시적으로 존재하고, 완료시 사라진다.
- 소요시간이 알 수도 있고 모를 수도 있어, 두 종류의 progree indicators가 존재한다:
  1. Determinate: well-defined duration, 파일 변환기
  2. Indeterminate: 계량불가능한 작업, 동기화작업

### Best practices

- 가능하다면 determinate progress indicator를 활용해라
- determinate를 활용할 때, 가능한 정확하게 진행현황을 보고하라
- progress indicator를 계속적으로 움직이도록 해서, 사용자가 작업 진행중임을 알 수 있도록 해라.
  - 작업이 stall되었을 때도 사용자에게 피드백을 주어라
- 원형에서 바 스타일로 바꾸지 마라
  - spinners와 progress bars는 다른 모양 및 사이즈를 지니고 있어, 한쪽에서 다른 한 쪽으로 변환되었을 때 혼동을 줄 수 있다.
- 도움이 된다면, 작업에 대한 추가 정보를 (정확하고 간결하게)비치하라
- 가능하다면, 사용자가 프로세싱을 일시정지 할 수 있도록 해라
  - Cancel 버튼과 함께 Pause button 제공
- 사용자에게 일시정지하였을 때 부정적인 결과가 있을 수도 있음을 알려라
  - cancel 혹은 일시정지 이전에 작업 결과물을 잃을 수도 있다면 alert를 주도록 한다.

### Platform considerations

- tvOS 추가사항 X

**<iOS, iPadOS>**

- 2가지 스타일

1. Progress Bar
   - leading side to the trailing side ⇒ 작업의 진행사항 표기
   - 항상 determinate in iOS and iPadOS!!
     - **UIProgressView**
2. Activity indicators
   - 작업이 진행 중일 때, 돌아감
   - 항상 indeterminate in iOS and iPADOS
     - **UIActivityIndicatorView**

- 네비게이션 바와 툴바에서 트랙의 채워지지 않은 부분은 가려라
  - progress bar를 페이지 로딩과 같은 곳에서 사용할 때, unfilled portion은 가리기
- Refresh content controls
  - 자동으로 내용 업데이트를 실행한다
    - 주기적으로 자동 업데이트를 실행하도록 한다.
  - 업데이트로 값이 추가 경우 짧은 제목을 제공한다
    - 선택적으로, refresh control이 제목을 포함할 수 있다. 대부분의 경우 필수적이지 않지만, 어떤 내용이 업데이트 되는지에 대한 정보를 입힌다.
      - 예시) Podcasts 같은 경우 가장 최신 업데이트가 언제 일어났는지를 보여준다.
      - **UIRefreshControl**

**<macOS>**

- 2가지 스타일이 있으며, 각각 determinate와 indeterminate 타입이 존재한다.

1. progress bars (bar indicators)
   - 가로 바 형태로 보여준다
   - Indeterminate: animated pulse가 있다.
   - **NSProgressIndicatorStyleBar**
2. Spinning indicators (spinners)
   - 원형 형태
   - Indeterminate: 돌아가는 애니메이션
   - **NSProgressIndicatorStyleSpinning**

- 공간이 제한적이거나, 백그라운드 작업의 상태를 확인하고자 할 때 spinning progress를 선호한다.
  - spinners가 작고 눈에 띄지 않아, 백그라운드 작업 확인이 용이
- spinning progress indicator에서 라벨링은 피해라
  - 사용자가 직접 실행하기에 라벨이 불필요하다

**<watchOS>**

- 3개의 스타일

1. Progress Bar
   - 항상 determinate
2. Progress rings
   - 항상 determinate
3. Activity indicators
   - 항상 indeterminate

- **ProgressView**



## Rating (-ing)