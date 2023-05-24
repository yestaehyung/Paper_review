
여기서 어떤 문제를 이야기 했는지, 접근 방법이 어떻게 되는지 정리해서 공유하기
논문에 활용할 수 있는지, 우리가 flow를 잘 체크해서 봐야할 것 같다.
저자가 학생이 아닌, 굉장히 추천 시스템을 많이 연구하는 사람이라서 우리가 논문을 잘 확인할 필요가 있을 것 같다.

우리 논문에 들어가는 말 XRS -> eXplainable Recommender System

-----

CHI LBW' 23

Abstract 

긍정적으로 or 부정적으로 편향된 설명이 어떻게 사용자가 최적의 추천을 고르게 할지 확인하는 실험프로토콜을 소개한다     
Preference elicitation stage
- allow for personalizing recommendation 
- Manual identification and extraction of item aspects from reviews 
- controlled method for introducing bias through the combination of both positive and negative aspects


Introduction

추천 시스템 -> 우리 생활에 큰 영향을 미치고, 중요하다.

설명은 user가 decision making을 할 때 중요한 영향을 미치는 것은 이미 알고 있다. 그런데 설명이 미치는 영향을 이해하고, 그것을 측정하는 것에 있어서는 아직 연구가 이루어 지지 않고 있다.    

다양한 설명에 대한 연구가 subjective question이 사람이 어떻게 추천을 인식하는지 했다.     
what is subjective question??    

**어떻게 정량적으로 설명이 사람이 만드는 선택에 영향을 주는지 측정하는 그런 것은 부족하였다. -> 우리 도 이야기 할 수 있을 것 같다.** 

A key diference to past work is that prior research has focused almost exclusively on explanations that highlight positive aspects of items,~~i.e., endorse a selection~~ , perhaps by drawing similarities to other items the user has previously indicated that they liked.    
-> 설명이 item의 긍적적인 측면에만 맞추어져 있다,     

Explanations can also help users make decisions by highlighting why not to select something. We perform the frst study that intentionally biases explanations towards positive or negative aspects of items in a controlled manner in the context of items where we have a prior understanding of which items users should fnd most relevant. We can thus quantify the degree to which positively or negatively biased explanations lead to users choosing suboptimal recommendations.     
-> 설명은 뭔가를 선택하고 싶지 않을 때 그러한 결정을 도와준다.     
이 논문에서 사용자가 어떤 item과 가장 관련이 있다고 생각해야 하는지에 대한 사전 이해가 있는 item의 context애서 item 긍정적 또는 부정적 측면에 대한 설명을 통제된 방식으로 의도적으로 편향시키는 첫 번째 연구를 수행합니다.   -> **조금 이해 안됨**     
이 실험은 긍정적이거나 부정적으로 편향된 설명이 사용자가 차선의 권장 사항을 선택하는 정도를 정량화할 수 있습니다.    

22 번 이전 연구에서 이야기 하였던 논문에서 영감을 받아서 수행, 그러나 negative 도 같이 본다는 것이 큰 차이점에 해당한다. 
	"(물론 긍정적인 정서로) 리뷰에서 자주 논의되고 사용자가 추천 아이템을 즐기도록 유도할 수 있는 일련의 특성을 얻기 위해 리뷰를 처리하고 분석했습니다 " -> 22번 논문     
	"설명의 목표는 사용자에게 item을 파는 것 뿐만 아니라, 사용자가 정보를 판단하도록 도움주는 것도 있다." -> 3번 논문     

어떻게 설명이 사용자의 결정에 영향을 주는지 정량적으로 측정하는 것이 RQ1 -> 근데 설명이 positive vs negative.   
다른 contribution은 사용자의 choices의 설명의 영향을 확인하는 정량적인 study protocol 실험 디자인을 제안하는 것도 있다.    

namely list of item vs natural language text를 한다. 

이 논문에서 기여하는 것은 explainable recommender system에 디자인에 기여할 것이다.     

-------






