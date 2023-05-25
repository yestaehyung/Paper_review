Introduction

이전의 연구는 설명이 사용자에게 ai의 조언이 틀릴지라도 더 들을 수 있도록 만든다는 것을 밝혀냄     

improving task performance를 하는 factors를 확인하는 것 
- AI 예측을 보여주는 것은 task performance를 중기 시킨다

AI prediction의 정확도를 보여주는 것은 user의 decision에 영향을 주는 것을 확인함    
Ai-related information(confidence and correctness)는 사용자의 decision making process에 큰 역할을 한다 그런데 실험 setting에 따라 다르게 영향을 미친다.     

human centered 측면에서 (적절한 설명 기술을 presenting 하고, selecting하는 것과 같은) 과 같은 연구도 있었음     
이런 연구들은 주로 알고리즘이나 설명의 presence and absence에 대한 것만 있었음    

그러나 만약에 다른 시각화를 통해 presented한다면 같은 기술이라도 다른 영향을 줄 수 있음       

최근의 연구들은 이러한 측면에 대해서 다루기 시작함, (ex contextualizing explanations or comparing visual, textual or hybrid explanations).   

이 논문에서는 설명에 의해 trigger 되는 reasoning에 초점을 맞춘다, 근데 presented data에 따라 주의 깊게 선택이 되지 않은 AI 제안에 대한 효율적이거나 비효율적인 이해  결과, ??  

inductive, abductive, deductive styles -> ???     

AI confidenct, explanation reasoning style (inductive, abductive, deductive).   


AI-related information in an XAI interface 기반 user study를 한다. 아래의 6가지를 고려한다     

a) the correctness of the AI suggestion    
b) AI confidence.   
c) explanations presented with logical reasoning styles.  

i) users' reliance on the XAI interface elements (stock charts, AI prediction, explanation).   
ii) users' task performance.   
iii) agreement with the AI.   

stock market domain -> 엄청 불확실한 도메인에서 decision making을 할 수 있음, 그리고 factor 가 적절하게 decision에 있어서 trust를 불러일으킬수 있음     


184명의 참가자를 대상으로, AI 가 조언을 해주는 trading platform을 사용(사고 팔 수 있음 4가지 주식을) - 사용자는 낮은 신뢰도 예측의 경우 인스턴스 데이터에 더 많이 의존하는 반면, 높은 신뢰도의 경우 AI 예측과 인스턴스 데이터에 똑같이 의존합니다.        

AI confidence가 높을 때 task performance에 abductive and deductive 한 설명 스타일이 주요한 긍정적인 영향을 주었다는 것을 확인함      

high AI confience + abductive or deductive style은 AI가 correct하면 예측한걸 동의하는 것을 증가 시킴     

- 우리는 confidence과 correctness 과 같은 AI 관련 요소가 의사 결정 과정에서 XAI 인터페이스의 인간 중심 속성, 특히 설명 추론 스타일과 상호 작용한다는 것을 보여줍니다. 한편으로, 설명의 질은 AI 예측의 신뢰도에 달려 있습니다. 반면에, 사용자는 효과적인 추론 스타일을 트리거하는 경우에만 이러한 정보를 받습니다.    
- 우리는 비전문가 사용자가 높은 불확실성 영역에서 결정할 때 XAI 인터페이스에 설명을 효과적으로 포함(또는 제외)하기 위한 일련의 지침을 제공하여 AI 신뢰도, AI 정확성, AI 정확성, 의사결정 프로세스(의존도, 합의 및 작업 수행)의 다양한 측면에 미치는 영향을 검증합니다, 다양한 설명 스타일이 있습니다.

------

inductive -> 귀납, abductive -> 귀추, deductive -> 연역    

Deductive reasoning(연)
# Study design

