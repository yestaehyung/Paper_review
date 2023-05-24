
여기서 어떤 문제를 이야기 했는지, 접근 방법이 어떻게 되는지 정리해서 공유하기
논문에 활용할 수 있는지, 우리가 flow를 잘 체크해서 봐야할 것 같다.
저자가 학생이 아닌, 굉장히 추천 시스템을 많이 연구하는 사람이라서 우리가 논문을 잘 확인할 필요가 있을 것 같다.


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
First study는 아이템의 negative, positive에 편향되게 설명을 한다. 


