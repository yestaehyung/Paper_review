
# Intro
여기서 관심 있는 것 -> one particular vertical market: garments and fashion products

Localizing fashion items, determining their category and attributes, establishing the degree of similariry to other products 

이전의 CV는 개인화를 고려하지 않지만, 이들의 예측과 임베딩을 추천 시스템에 활용할 수 있고, 과거에 사용자 선호도와 결합하여 희소성과 콜드 스타트 문제를 해결할수 있다.

## Fashion item representation

기존의 추천 시스템 (collabarative filtering, content-based filtering)이 있다, 제품을 표현하는 것을 학습하기 위해서는 많은 데이터가 필요로 하고, 고객이 패션 제품을 볼 때 어떤 점을 보는지(고려하는지) 학습하는 것은 어려운 일이다.

## Fashion item compatibility

아이템끼리 얼마나 어울리는지, 아이템 끼리 결합하는 작업, 
호환성 정보는 이미지, 텍스트 데이터를 사용하여 스타일적으로 유사한 제품을 일반화하는 방법을 학습
트렌드, 계절성, 위치, 소셜 그룹의 의존성이 예측에 어려움이 있다.

## Personalization and fit

추천하는 패션 제품은 장소, 계절, 행사, 문화적, 사회적 배경에 따라 달라진다. 이러한 요소를 발견하는 것이 어렵다. 요즘 연구는 대규모 SNS 데이터에서 이러한 요소를 뽑아내려고 한다. 
체형 또한 스타일 선택에 영향을 줄 수 있다. 

## Interepretability and Explanation

패션 추천 시스템을 사람들에게 설명할 수 있게 배치하면, 사용자의 신뢰를 높이고 쇼핑 환경을 높일 수 있다.

## Dsicovering Trends 

소비자의 선호도를 예측할 수 있는 능력이 중요하다. 여기서도 소셜 미디어를 활용하여 연구를 진행한다. 



![](https://i.imgur.com/JVGg6hP.png)

# Categorization based on task

## Fashion item recommendation

사용자의 선호에 맞는 individual fashon items을 추천하는하는 것에 집중

![](https://i.imgur.com/wE59frv.png)

가장 간단한 CF(collaborative filtering) model은 BPR-MF 이고, 많은 모델 기반이 된다.

BPR - 클릭 이나 구매와 같은 implicit-feedback 하에서 추천 문제를 다룬다. 추천은 user가 선호할만한 item 목록을 예측하는 것을 의미함, 이 논문은 베이지안 추론에 기반한 최적화 기법을 제공하여, item에 대한 선호 강도를 반영할 수 있또록 함,  [정리바로가기](https://leehyejin91.github.io/post-bpr/) (추후에 정리 예정)

## Fashion pair and outfit recommendation

Fashion outfits은 같이 입은 N개 item의 집합,
온라인 fashion store의 일반적인 outfits 은 different categories로 구성되어 있다.

![](https://i.imgur.com/mJ7eeIg.png)

s -> outfit utility function 