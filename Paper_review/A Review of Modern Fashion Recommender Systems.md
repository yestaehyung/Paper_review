
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

**2.1 에서 fashion recommender system을 categorize하고 
2.2 에서 task input data를 확인**outfit recommendation

Fashion outfits은 같이 입은 N개 item의 집합,
온라인 fashion store의 일반적인 outfits 은 different categories로 구성되어 있다.

![](https://i.imgur.com/mJ7eeIg.png)

s -> outfit utility function, item들끼리의 조합이 얼마나 잘어울리는지 계산하는 function
FITB, outfit compatibility score prediction으로 주로 평가를 한다.
이러한 function을 계산할 때 도메인 정보를 활용할 수도 있다. 

fashion item을 추천하거나 outfit을 추천할 때 아래와 같은 어려움이 있다.

### Personalizing to a target customer

개인화된 의상 모델을 학습하는데 데이터가 충분하지 않다.
이러한 문제를 해결하기 위해서 fashion generation, graph-learning, binary codes, self attention과 같은 방법을 사용하고 있다.

### Modeling outfits as a sequence

LSTM과 같은 sequence model을 활용하여 outfit을 item의 sequence 로 접근
**본 논문에서는 text 쿼리, image 쿼리를 허용해서 문제를 일반화 할 수있다고 함.
만약에 쿼리가 image인 경우 visual retreival or contextual recommendation이 될 수 있다고 한다**

### Content-based versus collaborative filtering

패션 아이템 추천 task는 visual이나 text 정보를 포함할수도 있고 안할수도 있는 CF 방법론이 대부분
outfit 추천과 같은 경우는 content based로 주로 접근이 되어 왔다. -> visual metric learning 과 같은 방식
근데 이런 content based로 접근을 한 이유는 outfit data에 대한 부족이란 것이 있음 
