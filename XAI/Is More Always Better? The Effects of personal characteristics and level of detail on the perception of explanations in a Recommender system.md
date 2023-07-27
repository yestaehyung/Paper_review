
# Intro

Explainability of RS는 최근에 관심이 증가한 부분, 개인화된 추천 알고리즘에 대해서 추천 결과와 왜 아이템이 추천되었는지 설명을 같이 주는 것이 xRS이다.    


아래 4가지를 집중적으로 설명가능한 추천 시스템 연구에서 봐왔음    
(a) explanation goal (e.g. transparency, scrutability, trust, effectivness, persuasiveness, efficiency, satisfaction).       
(b) explanation style (e.g. content-based, collaborative-based, social, hybrid)    
(c) explanation scope (i.e. input: user model, process: algorithm, output: recommendation items)  
(d) explanation format (e.g. textual, visual)    

이것 이외에도 설명을 end-user에게 어느 level까지 해주어야하는지에 대해 논의가 이루어져 왔음.  
이렇게 다른 설명들은 explanation goal과 user의 type에 영향을 줌      
그런데 사용자들은 제공하는 모든 설명의 정보에 관심이 없을수도 있음    
다른 유저는 다른 needs가 있을 것이기 때문에 만약에 사용자가 설명이 이해가 되지 않는다면, 설명이 오히려 부정적인 영향을 줄 수 있음 (너무 많이 생각을 하게 된다, 내가 알던것과 달라서 혼란이 온다, 신뢰가 부족하다)     

설명 가능한 RS에서 이런 휴먼 팩터와 행동을 최근 연구에서 보기 시작하였음    
이런 연구는 개인의 특성이 설명의 perception이나 다른 설명으로 인해 선택을 바꾸는 동기를 제공하는 것에 영향을 줄수 있다고 보고 하고 있음    

그런데 지금까지의 이런 연구들은 대부분 one-size-fits-all으로 접근하고 이는 각기 다른 유저의 선호나 니즈를 다루지 않음    (one-size-fits-all: 모두에게 적합한 알고리즘이라 생각하면 될듯)     

설명은 개인화되어야한다는 연구와 설명가능한 RS는 올바른 사용자 그룹에 대해 올바른 설명을 제공해야한다는 이전 연구를 바탕으로 one-size-fits-all 에서 personalized 으로 xRS를 옮겨가야한다.         

이 논문에서 설명의 디테일한 level에 탐구하려고 한다. 설명의 정도와 개인의 특성을 분리해서 user study를 수행한다. 이걸 위해 RIMA라는 개인화된 추천 설명을 세가지 정도로 나누어 제공하는 서비스를 만듦.    

RQ: 어떻게 개인의 특성이 사용자의 설명의 detail level에 따라서 user perception에 영향을 미칠수 있을까?

결과는    
(1) 다른 유저에게 설명의 다른 정도를 제공하는 것이 중요하다.    
(2) 설명은 특정한 설명의 목표와 특정한 유저의 타입에 따라 다르게 디자인되어야한다.    
(3) 설명의 내용은 사용자의 data를 다뤄야한다.     

# RW

## Explanation with different levels of detail

- 다른 user group은 XAI를 사용하는 동안 다른 목표를 가지고 있음.     
- 특정한 recommendation을 생성하는 정확한 algo를 제공하는 것이 반드시 좋은 설명은 아니다.
- 사람들은 설명의 질을 판단하는 것이 아닌 얼마나 유용한지 판단하는 경향이 있음
- 사용자의 인식 정도가 설명의 이해에 영향을 미침
- 디테일한 설명이 자동적으로 higher한 신뢰와 만족을 얻지는 않았음, 추가적인 설명을 이해하기 위해 더 노력을 해야했기 때문임.     


