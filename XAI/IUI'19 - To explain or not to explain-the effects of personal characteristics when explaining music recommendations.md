
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
몇몇의 연구자들만이 시각화의 perception와 개인 특성의 관계를 확인했는데, 이 연구들은 RS 설명에 focus되어 있지는 않았다.     

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

## Personal characteristic 

아직 visualisation 관련해서 개인의 특성을 본적은 있으나, 추천의 설명 관련해서 개인의 특성과 추천 시스템의 관계를 이해하려했던 논문은 없었다.      

- Locus of Control (통제 위치)
	- 사람들이 그들의 삶에서 일어나는 일들에 대해 자신들이 힘을 가지고 있다고 믿는  -> 내가 얼마나 통제할 수 있는지? 
	- LOC test를 아래 논문에서 사용한 거로 수행함, 개인이 결과에 대해 통제할 수 있는 정도를 
- Need for Cognition
- Visualisation Literacy
- Visual Working Memory
- Musical Experience
- Tech-Savvines