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


Inductive reasoning (귀납적 추론)    
특정한 것에서 일반적인 것으로 이동하여 결론을 도출하는 방법, 연역적인 추론과 대조된다.     

특징 관찰 - Nala는 주황색 고양이이며 큰 소리로 가르랑거립니다.    
패턴 인식 - 내가 만난 모든 주황색 고양이는 큰 소리로 가르랑 거린다.    
일반적인 결론 - 모든 주황색 고양이는 큰 소리로 가르랑 거린다.    

abductive reasoning (귀추법)    
가정을 선택하는 추론의 한 방법, 만약 사실이라면 관계있는 증거를 가장 잘 설명할 것 같은 가정을 선택하는 방법이다. 귀추법에 의한 논증은 주어진 사실들로부터 시작해서 가장 그럴듯한 혹은 최선의 설명을 추론한다.     

Deductive reasoning(연역적 추론)    
일반적인 아이디어에서 특정 결론으로 진행하는 논리적인 접근방식, 전제로 시작해서 다른 전제를 추가함, 이 두가지 전제를 바탕으로 결론을 내린다. '전제-전제-결론'의 방식을 따른다    

전제 - 모든 곤충은 정확히 6개의 다리를 가지고 있습니다.    
전제 - 거미는 다리가 여덟개 입니다.    
결론 - 그러므로 거미는 곤충이 아닙니다.    

연역법

연역적 추론(Deductive reasoning)은 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)가 �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)의 형식 논리적 결과일 때만, �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)로부터 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)를 추론하는 방법이다. 즉, 연역법은 가정의 결과를 이끌어내는 과정을 말한다. 가정이 참이라고 주어졌을 때, 타당한 연역 추론은 결과가 참이라는 것을 보장한다. 예를 들어 "위키는 누구나 수정할 수 있다" (�1![a_{1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bbf42ecda092975c9c69dae84e16182ba5fe2e07)) 와 "위키피디아는 위키이다" (�2![a_{2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/270580da7333505d9b73697417d0543c43c98b9f))가 주어졌을 때, "위키피디아는 누구나 수정할 수 있다" (�![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)) 가 뒤따른다.

귀납법

귀납적 추론(Inductive reasoning)은 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)가 반드시 �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)로부터 뒤따르지 않더라도, �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)로부터 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)를 추론하는 방법이다. �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)는 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)를 받아들이기 위한 아주 좋은 이유가 될 수 있지만, 반드시 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)를 보장하지는 않는다. 예를 들어, 이때까지 관찰된 모든 백조가 하얗다면, 귀납적으로 모든 백조가 하얗다고 추론하는 것은 그럴싸하다. 전제로부터 이끌어낸 결론을 믿을 좋은 이유가 있지만, 결론의 참을 보장하지 못한다. (실제로, 어떤 백조는 까맣다는 것이 발견되었다)

귀추법

귀추적 추론(Abductive reasoning)은 �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)를 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)의 설명으로 추론하는 방법이다. 이 추론의 결과로, 귀추법은 결과 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)로부터 전제조건 �![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)가 추론되도록 한다. [연역 추론](https://ko.wikipedia.org/wiki/%EC%97%B0%EC%97%AD_%EC%B6%94%EB%A1%A0 "연역 추론")과 귀추법은 "�![a](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc)는 �![b](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3)를 수반한다"라는 규칙을 이용해 추론할 때 방향이 다르다.
# Study design

우리는 참가자들에게 사례(지표가 있는 주식 차트), AI 예측 및 예측 신뢰도(즉, AI 불확실성을 신뢰도 백분율로 표현)와 고려된 네 가지 설명 방식(설명 없음, 귀납적, 귀납적, 연역적) 중 하나를 제공하여 주식을 사고파는 결정을 내릴 것을 요청했습니다.         

### Independent variables

Explanation type
- no explanation
- inductive
- abductive
- deductive

AI confidence
- low
- high

AI correctness
- wrong
- correct

### Dependent variables

- 지표가 포함된 주식 차트, AI 정보, 순위로 측정된 설명 -  사용자에게 제공되는 다양한 유형의 정보에 대한 사용자의 의존도
- 사용자가 현재 주식에 할당하기로 결정한 작업이 올바른지 여부(금전적인 이익이 되는지) - 작업 성과
- 사용자가 자신의 결정으로 AI 예측을 확인하는지 여부를 AI와 동의하는지?    

Datasets    
- 야후 경제에서 접근 가능한 4개의 다른 일일 주식 정보를 선택 (2017년 5월에서 2022년 8월까지)
- 모델의 정확도가 70%이상 precision, recall, f1 score과 같은 기준을 고려ㅐ해서 500개 중에서 4개를 선택함
- 5년 범위의 데이터를 가지고 모델을 학습함, 그것이 성능에 있어서 가장 적절하였고 그리고 거래 경험이 없는 경우 과거 차트에 대한 분석을 하기 힘들기 때문에, 만약 20년 이상의 데이터를 학습할 수 있는 사람이라면 그자체로 편향이 이루어진다. 그런데 너무 짧은 경우는 또 힘들다. 

Classification problem
- RF를 사용함, 다른 지표를 feature로 사용하여 4개 주식 각각에 대해 하나의 RF 모델을 학습함
- RSI, STOCH, ADC, MACD, POC, OB, MOMU, the Daily News Sentiment Index, the Ease of Movement, the 200-day moving average
- look-ahead bias를 피하기 위해, datasetdmf 85 / 15로 나누어서 학습을 하였다
- 300개의 tree를 사용하였고, 각 노드의 최소 sample 수는 6개로 하였다. 
- Recursive Feature Elimination으로 성능을 향상 시키고, feature의 수를 12개에서 5개로 줄였다. 
	- MACD
	- ATR
	- EMV
	- RSI
	- News Sentiment
- test set의 정확도는 71%로 다른 최신 연구와 비교하였을 때 괜찮은 성능이다. 

Instance selection
- AI confidence와 correctness의 조합 4가지를 선택한다
	- low - correct
	- low - wrong
	- high - correct
	- high - wrong
- 각자의 참가자 들에게 무작위로 reasoning style을 할당한다
- AI prediction을 계산한다. 
- Instance를 선택하는데 있어서, 아래의 과정을 따름
	- 1) Epistemic uncertainty만 고려하고, 0 ~ 100 범위의 confidence score로 변환해서 4개 주식에 대해 Model Agnostic confidence estimator를 사용해서 수정된 RF 모델에 대한 AI Confidence를 계산 
	- 2) 각 주식에 대해 사분위수를 계산하고, 두번째 사분위수를 사용해서 높은 AI 신뢰도와 낮은 AI 신뢰도에 대한 임계값을 선정
		- 두번째 사분위수 값은 57%이고 각 주식에 대해 신뢰 점수 분포는 유사함
		- thr 보다 작으면 낮은 AI 신뢰도에 인스턴스를 할당하는 것 
	- 3) 각 종목 별로 16개의 낮은 AI 신뢰도와 16개의 높은 AI 신뢰도 사례를 무작위로 선정함
		- 각 세트에는 AI 가 정확한 예측을 하는 8개 사례와 AI가 틀린 8개의 사례가 포함되어 있음
		- 최종 낮은 신뢰도는 12% ~ 55%, 높은 신뢰도는 75% ~ 90% 사이임

설명 생성
- 귀납적 설명
	- MACEst 내부에서 K-nn 알고리즘으로 검색한 local example-based explanations를 선택함
	- XAI 연구에서 많이 사용되는 방식이다.
	- 테스트 사례가 주어지면 아래의 요소를 보여주는 표를 통해 훈련 세트에서 가장 가까운 3개의 n을 보여준다. 
		- 이웃 example의 날짜
		- 주식 가격
		- 지표의 값
		- 이웃 sample 의 가격 증가/감소 
	- -> 이전의 사례들은 이랬을 거니까 너가 예측하는 것도 이럴 것이다 라는 방식
- 귀추 방식
	- SHAP framework를 사용함
		- 최종 예측에 찬성하거나 반대하는 각 기능의 기여도를 계산해서 예측에 대한 설명을 생성함 
		- Shapley 값으로 얻은 예측에서 각 특징의 가중치를 표의 배경색에 mapping 함
		- 가격 상승에 기여한다면 빨간색으로, 내려가면 파란색으로 표시함
		- 밝을 수록 AI의 결정에 중요한 역할을 했다는 것 
- 연역적 방식
	- CHIRPS 라는 알고리즘을 사용함

Procedure

Pulsive platform2를 사용하여 주식 시장 거래 과제에 대한 온라인 사용자 연구를 수행함

1. 참가자들은 연구에 대한 간략한 설명이 포함된 문서를 읽고 안내된 동의서를 작성함
2. 테스트는 참가자들에게 과제를 완료할 때 천천히 시간을 갖고 주식을 소요하고 이익을 내는 것을 상상해 보라고 하는 거래 과제를 소개함
	1. 모든 정답에 대한 보너스 지급을 설정해서 이익에 포함시킴 
	2. XAI 인터페이스를 설명하는 짧은 길이의 동영상을 보여줌, 하는 도중에도 볼 수 있게함
3. 4가지 거래 과제를 수행
	1. 두가지 작업은 buy하는 거고 두가지는 sell하는 것
	2. 참가자는 100달러의 예산을 가지고 시작함
	3. 과거의 가격 정보, 지표, AI의 조언, 설명을 고려해서 해당 기업의 주식 매입에 투자할지 말지 결정해야함
	4. buy를 할 떄 1주에 100불의 가치를 가지는 주식을 사야한다. sell 할 때는 구매할 때랑 동일 정보를 사용해서 팔지 말지 결정해야한다. 
	5. 작업이 끝나고 4개의 질문을 수행함

250명의 참가자를 모집해서 사용자들로부터 1000개의 decision을 수행함, 여기서 735개로 거른듯,,?    
4가지의 작업은 25분으로 수행이 되고, 시간당 보상은 12파운드, 정확하게 예측하면 0.5 파운드 추가함    

최종적으로 734개의 인스턴스를 고려함   
4가지 질문
- 주식 거래 경험: "주식을 거래해본 경험이 있음?" 
	- 경험 없음, 경험이 적음, 경험이 풍부함, 매우 경험이 풍부함
- 신뢰도: XAI 인터페이스에 포함된 정보의 순위, decision을 내릴 때 얼마나 도움이 되었는지 순위를 매김
	- A) 지표가 있는 차트
	- B) AI 정보 
	- C) 설명
- 과제 수행
	- 참가자의 최종 결정이 올바른지, 
- 참가자의 최종 결정이 AI 예측과 일치하는 지 여부


![](https://i.imgur.com/SZoqc6Y.png)

----
# Hypotheses

실험자에게 어떤 유형이 가장 도움이 되었는지 순위를 매겨달라고 요청함   
도메인 지식이 낮은 참가자를 고려함   
- 이전 연구는 비전문가 참가자가 AI가 지원을 해줄 때 과도한 신뢰를 보이거나, 그냥 AI에게 위임을 해버리는 것을 보여줌

위의 이런 사실로 보았을 때, 참가자가들이 일단 자신의 판단을 믿고, 주식 차트랑 지표를 과하게 사용할 수도 있음, 반대로 생각하면 참가자가 인공지능에 과하게 의존하면 인공지능의 에측이 주된 정보원임     

이전 연구에서는 설명이 참가자의 의존성을 증가시키는 역할을 한다는 것을 확인함    

이 논문에서는 AI를 신뢰하는 정도가 시스템에 대해 과도하게 의존하는지 아닌지 영향을 미칠 거능성이     


### H1: XAI 인터페이스에서 제공되는 정보에 대한 사용자의 신뢰도는 AI 신뢰도 수준에 따라 달라진다.
### H1a: AI 신뢰도가 낮을 때, 사용자는 주로 지표가 있는 차트에 의존하고, 그 다음에 설명 혹은 AI 에측에 의존한다

### H2: 사용자의 작업 성과는 AI 신뢰도와 설명 스타일 간의 상호 작용에 의해 조절이 된다.
### H2a: AI 신뢰도가 높을 때, abductive explain style은 inductive와 비교해서,더 높은 task preformance를 보여준다
### H2b: AI confidence가 높을 때, deductive explain style은 inductive와 비교해서 higher task performance를 보여준다.

### H3: 사용자의 동의는 AI correctness, AI confidence and explain style 간의 상호 작용에 의해 조정이 된다
### H3a: AI 신뢰도가 높을 때, AI 정확성이 높다


