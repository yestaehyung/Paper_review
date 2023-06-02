
https://dl.acm.org/doi/pdf/10.1145/3301275.3302313

Abstract 

추천 시스템의 모델은 black box 임, 개인화된 추천을 제공하는 것에 대해 논리적인 이유가 사용자들에게 설명이 되지 않기 떄문    
최근에 이러한 이슈를 다루기 위해 다양한 논문이 있었음, 사용자들이 추천의 원인을 찾을 수 있게 하는 다음을 제공해서->  textual explanations or interactive visualisations         
이러한 방법이 효과가 있다는 것도 확인하였음    
이전 연구는 또한 개인 특성이 perceived benefits에 효과적인 역할을 한다는 것을 확인함     
그러나 추천을 설명하는데 있어서, 개인 특성의 효과에 대해 살펴본 연구는 적다     
이 연구에서는 설명이 있는 음악 추천 시스템을 개발, within-subject 로 user study를 수행하였다. 참가자들의 개인적인 특성 확인하고, 정성정, 정량적인 평가 방법을 수행함     

결과는 개인적인 특성이  추천 시스템의 인식과 상호작용 부분에 있어서 중요한 영향을 준다는 것을 확인함     
Cognition에 대해 low need 인 사람들 -> recommendations을 설명하는 것이 가장 효과적임     
Cognition에 대해 high need 인 사람들 -> 설명이 lack of confidence를 만들 수 있음    

----

논리의 흐름 

추천 시스템은 black box이기 떄문에 사용자가 왜 추천되었는지 알기 힘듦, 그래서 설명이나 visual적으로 interaction하는 것을 통해 사용자가 왜 추천이 되었는지 확인하는 연구가 있었음, 그러나 조금더 개인적인 관점에서 개인의 특성이 설명에 어떤 영향을 보았는지 확인한 논문은 없었음, 그래서 우리가 user study를 통해 확인하려함     

# Introduction

Each to his own: how different users call for different interaction methods in recommender systems.    
-> 세세한 개인적인 특성(도메인 지식)과 추천 시스템에서 선호하는 interaction 방법이 있는지 확인한 논문     

음악 추천에서 개인적인 특성, controllability 의 영향이 미치는지 accptance, preceived diversity and trust 쪽에서 살펴 왔었다.     
최근에는 사용자에게 RS의 inner process를 설명하는 연구가 있었음     
- 현재 있는 RS는 사용자에게 투명하지 않기 때문에, 근거에 기반한 decision을 만들기 힘들다 주장함
	- 사용자에게 visual 설명을 제공하는 Film RS를 만듦, 
- 음악 추천 도메인에서, TasteWeights는 사용자가 좋아하는 아티스트와 추천 트렌드 아이템의 관계를 시각화하여 제공함 

However, to the best of our knowledge, 이전의 연구는 개인의 특성이 미치는 영향을 조사하지는 않았다.     
몇몇의 연구자들만이 시각화의 perception와 개인 특성의 관계를 확인했는데, 이 연구들은 RS 설명에 focus 되어 있지는 않았다.     

**본 연구에서는 within subject로  user study를 수행, 설명이 있고-설명이 없는 추천 시스템에 대해서 개인 특성의 영향을 확인하는 스터디임**     

확인한 개인적인 특성은 
- personality trait
- variety of cognitive skills
- abilities related to the specific task of using music RS

RQ1: 어떻게 개인적인 특성이 추천이 설명 될 때 user perception 에 영향을 미치는 가?      
RQ2: 어떻게 개인적인 특성이 추천이 설명 될 때 user interaction 에 영향을 미치는 가?      


결과      
- explanations are raising the confidence of users with a low need for cognition in contrast to users with a high need for cognition.

1. address the gap between the research about personal characteristics and the research about explanations in RS
2. provide evidence that personal characteristics have a significant influence on the interaction and perception of explanations

----
# RW

우리는 어떤 PC를 사용할지 정할 필요가 있음, fashion domain이나 인식에 있어서 가져오면 좋을 것 같음.     
다 살펴보지는 않았지만, 우리는 실생활에 적용된다는 점에서 더 의미가 있으며, 소비자의 구매 과정? 과 같은 조금 더 패션 이커머스쪽의 PC를 찾아서 RW에 적으면 좋을 듯함     

## Personal characteristic 

아직 visualisation 관련해서 개인의 특성을 본적은 있으나, 추천의 설명 관련해서 개인의 특성과 추천 시스템의 관계를 이해하려했던 논문은 없었다.      

- Locus of Control (통제 위치)
	- 사람들이 그들의 삶에서 일어나는 일들에 대해 자신들이 힘을 가지고 있다고 믿는  -> 내가 얼마나 통제할 수 있는지? 
	- LOC test를 아래 논문에서 사용한 거로 수행함, 개인이 결과에 대해 인지하는 통제의 정도를 측정
		- Generalized expectancies for internal versus external control of reinforcement
	- 사회 심리학에서 제시한 개념, 살아오면서 자신의 영향력 밖에 있는 외력에 대항하여 사건의 결과를 스스로 통제해 왔다고 믿는 정도
	- LOC는 이번 실험에서 중요한 역할을 하는데, 실험 시스템에서 추천 과정을 조정하는 옵션을 제공하기 떄문임
- Need for Cognition
	- 인식 기술은 다양한 이전 연구에서 사용이 되어왔다. 
	- cognitive skill을 측정하는 것과 다르게, need for cognition은 개인이 노력하는 인지활동에 참여하고 즐기는 경향의 척도이다.
	- 아래 논문에서는 NFC를 test하는 설문을 보여줌, 18개의 질문을 5-point Likert scale로 하는 것 
		- The efficient assessment of need for cognition
	- 여기서 NFC를 사용한 이유는 참가자들의 다양한 상황에서 플레이 리스트를 만들 떄, 인터페이스 구성 요소를 사용하려는지 그러한 의지를 확인하기 위해서임
- Visualisation Literacy (VisLit)
	- 이미지와 그래프의 형식으로 부터 보여지는 정보의 의미를 해석하는 능력
	- 아래 논문에서 VisLit를 체크하는 설문을 만듦, 데이터를 변환하고 시각적 패턴을 해석하기 위해 그래프를 자신 있게 사용할 수 있는 개인의 능력을 포착하는 방식으로 설계
	- 여기서는 특정 bar charts의 test designed 을 선택함, 왜냐하면 bar chart를 설명하는데 많이 사용하여서
- Visual Working Memory
	- cognitive system에 한 부분으로 더 미래의 processing을 위한 짧은 기간에 정보를 얼마나 기억할 수 있는지에 대한 것
	- visual, verbal working memory로 될 수 있음
	- visual working memory 는 visual information system과 상호작용할 때 cognitive load에 영향을 줄 수 있음
	- 여기 스터디에서는 visually explaining recommendations에 focus하기 때문에, visual working memory를 측정함
	- Corsi block-tapping technique로 측정
- Musical Experience (우리 논문에서는 Fashion Experience)
	- 음악 경험은 음악 추천 시스템과 사용자가 어떻게 상호작용을 할지 영향을 미침
	- Goldsmiths Musical Sophistication Index (Gold-MSI)는 사용자의 도메인 지식을 측정하는 효율적인 방식 그리고 성격과 음악선호간에 강한 코릴레이션을 보여준다.
	- 음악 추천에 대한 이전 연구도 Gold-MSI를 PC를 측정하는데 사용하였다.
- Tech-Savviness
	- 여기서 정의한듯?
	- 참가자들의 tech-savviness를 새로운 기술에 대해 시도해보려는 자신감으로 정의함
	- internet-savviness와 같은 용어로 이전 연구에서 사용을 한적이 있었음
		- 이런 연구는 새로운 기술을 믿고 쓰려는 것보다는 참가자의 인터넷 친숙도를 측정하려 하는 것에 집중함
	- 참가자들이 새로운 음악 추천 인터페이스와 얼마나 잘 상호작용하는지 확인할 수 있는 중요한 요소라고 생각해서 사용함
	- we captured tech-savviness by asking the participants to identify themselves between confident, not confident and somewhere in-between when it comes to trying new technology.

## Explanations in Recommender Systems 

추천 시스템은 사용자가 좋아할 것만 같은 아이템을 예측하는 여러 알고리즘에 의존함     

다양한 알고리즘들이 최고의 가능한 제안을 주기 위해 노력함, 그런데 투명하지 않은 알고라즘들      
이건 문제가 될 수 있는데, 왜 특정한 추천이 제공이 되었는지 이해가 안되면 추천에 대해 의심할 수 있게 되버린다.     

그래서 아래 논문에서는 설명을 하기 위한 지표로 7가지를 제시함
- A survey of explanations in recommender systems
- Transparency
- Scrutability
- Trust
- Effectiveness
- Persuasiveness
- Efficiency
- Statisfaction

설명을 하는 타입은 아래의 세가지가 있음
- Content-based explanation
	- We have recommended X because you liked Y 
- Collaborate based explanation
	- People who liked X also liked Y
- Preference based explanation
	- Your interests suggest that you would like X

Textual 설명에 대해서는 다양한 연구가 visual적인 설명을 보고 있다.      
Interactive visualisations 는 사용자가 이해하고, 추천이 보여지는 방법에 영향을 미치는 components를 조작할 수도 있음     

PeerChooser -> 사용자에게 추천 process에 대한 visual 설명을 제공하고, input weight를 조작할 수있는 기회를 준 연구       
Small World -> social recommender system, 추천이 되는 사용자끼리의 social connection을 node-link diagram을 사용해서 visual적으로 시각화 함      
SFViz -> radial space-filling texhnique



# Intro 정리

## 연구 배경

### 추천 시스템 배경
- 