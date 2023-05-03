실험 중심으로 H에게 업데이트

중요하다고 생각되는 부분 붙여넣기

ABSTRCT
Consequently, we suggest that RS should provide richer explanations in order to increase their perceived recommendation quality and trustworthiness.

INTRODUCTION

## RS에서 문제 상황
온라인 플랫폼은 impersonal한 추천 시스템에 의존하고 있다. 이러한 추천은 너문 많은 대안이 있을 떄 사용자의 의사결정을 도와주는 역할을 한다.   
시스템의 정확도가 높아도, black box이기 때문에 사용자의 detail을 다루지 못할 수도 있고, 결과적으로 unfitting한 mental model을 생성할 수도 있다. 그러면 추천 시스템을 거부하고 신뢰하지 않을 수 있다.   

## trust 를 보는 이유?
그래서 몇몇의 연구자들은 RS의 퀄리티를 확인할 때,  RS의 truth-worthiness 를 고려해야한다고 한다. 

그런데 RS는 trust를 증가시킬 때 중요한 human properties가 부족하다, 그리고 이건 사용자가 bonds를 어떻게든 형성하게 어렵게 만든다. 이걸 완화하기 위해서 social components의 introduce를 into RS하는게 좋다. -> 이런걸 반영하는 웹 사이트가 있다: 사람이 만든 추천과 자동추천을 섞어놓은 경우(사람이 review를 작성하는 것과 같은 것)      

**그러니까 사람이 리뷰를 남기는 것과 같이 추천에 도움이 될 수 있는 요소를 추가하는 것 -> 신뢰 향상에 도움이 된다.**        

근데 내가 생각했을 때 약간 당연한 걸 확인하는 느낌..?

그래서 RS를 디자인하는 사람들은 투명성과 신뢰성을 높이기 위해서 text 기반의 설명을 추가한다.
- 사용자가 최근에 본 상품과 추천 상품의 유사성을 나타내는 것
- 'User who bought ... ' 
- 이러한 간단한 질문이 효과가 있는지 질문이 계속되었음, 그래서 richer explanintions와 비교
	- 어떻게 trustworthiness and influential factors의 인식 차이가 있는지 확인


이 논문에서 저자들이 주장하는 것
- 지나치게 단순한 설명이 추천 소스에 대한 신뢰를 확립하는데 관련한 표현력과 사회적 특성이 부족하다?
	- 이 주장을 뒷받침하기 위해 user study를 수행함
		- 참가자들이 다른 사람이나 일반적인 RS에 의해 선택된 권장사항을 평가하도록 하는 study
		- 추천 결과에는 RS에 대한 개인적인 조건 또는 유사성 기반에 대한 설명이 구성되어 있음
	- By utilizing tools of causal statistical inference, i.e. structural equation modeling [33] and the counterfactual framework [18, 35, 40] -> 이걸 수행해서 충분한 설명이 신뢰 구축 과정에 큰 역할을 한다는 것을 확인하였다. 
결과적으로 인간이 정보를 교환하는 방식을 모방하는 설명할 수 있는 컴포넌트를 RS 개발할 때 더하는 것은 합리적이다.

반사실적 분석은 우리를 RS가 어떤 것을 해야하는 가설적인 상황에 대한 답변을 할 수 있도록 도와준다.
- 다른 알고리즘의 변화 없이 유사도 기반의 설명을 인간과 같은 설명으로 대체 하는 것은 추천의 기대되는 품질을 13%향상 시켰습니다. 

여기의 참가자들은 이주동안 두개의 추천을 받는다. -> 저자들이 신뢰 개발을 그 시간동안 접근할 수 있게 한다. 
인간에 대한 신뢰는 변하지 않았지만, 자동화된 상대에 대한 신회는 약간 감소하는 것을 확인함. 

Contribution
- User study했는데, personal VS impersonal, 이건 그룹에 따라 어떻게 perceived 하는지, 어떻게 신뢰가 만들어 지는지 확인할 수 있었다.
- explanation quality, recommendation quality, social presence, trustworthiness 사이의 복잡한 의존성을 밝혀내었다.
- RS가 그들의 의견을 설명하는 것을 더 잘 갖추고 있어야함을 제안

Personal vs Impersonal 차이를 확인하기 위해 between subject online study를 수행하였다. 
- between subject online study -> 다른 사람이 각각 컨디션이 다른걸 사용, 각 사람은 한개의 interface만 사용한다. 

영화 추천 하는 것, 
- 영화로 선택한 이유
	- 사람들이 domain에  친숙했으면 좋았을 것 같음 -> 그래야 추천을 해줄 수 있다
	- automatic RS dataset이 잘 구축되어 있다는 것

영화를 보길 원하기 때문에 Amazon prime을 보유하고 있는 393 명의 참가자를 모집

실험 참가자는 93명
- 55 여자, M = 25.75, SD = 9.00 의 나이, 학생(68%), 직장인(24%)
- 아마존 프라임 계정을 가지고 있어서 추천한 영화를 볼 수 있어야함
- daily(41%), weekly(31%)로 online streaming을 사용해야함
- 49명은 personal에 44명은 impersonal에 배정함

참가자들은 독립된 컨디션에서 10개의 영화를 평점 매긴다. 
- 5-point 점수로 선호 평가 

그리고 Figure 1의 실험 구조를 따름
![](https://i.imgur.com/TOArMnw.png)

Impersonal Condition
- 참가자들이 평점을 매기고 나서 즉시 영화에 대해 추천을 받게 됨
- 추천은 Matrix Factorization 기술로 이루어지고 개발은  java로 진행함
- 추천에 대해 유사도 기반 설명이 같이 보여진다. 
- Fight Club 이 추천되고 Pulp Fiction이 사용자가 높게 평점을 매겼으면 설명은 아래와 같음
	- Fight club is recommended to you because it is very similar to Pulp Fiction
- 이렇게 추천과 설명을 받고 나서 참가자들은 영화를 보는 것을 요청 받았고, 추천과 설명에 대해 5-Point scale로 평가를 함
- 다시 이 과정을 반복하는 과정을 거침 

Personal Condition
- 모든 참가자들은 buddy를 할당 받는다. 
	- buddy: In general this assignment was random but we controlled it for avoiding reciprocal relations. Participants received recommendations from a different person as they were providing recommendations to.
- 393명은 추천을 해주는 사람들로 모두 아마존 프라임이 사용 가능한 사람들
- 393명 중에서 참가자는 한명을 추천을 위해 고르고 왜 그들이 추천을 했는지에 대한 설명을 받는다
	- 이 설명은 255 글자로 제한, impersonal과 비슷하게 유지하기 위해

웹사이트를 제작, impersonal, personal 모두 같은 사이트에서 진행
2주가 지나고 나서 참가자들은 질문을 채우는 것을 요청받았다. 
시스템에 로그인하고 나서 preference elicitation을 하기 전에, 참가자들은 general demographics에 대한 첫번째 질문을 받았다.   
질문 한개 더 함, 
![](https://i.imgur.com/NxrhHZI.png)

구조 방정식 모델링을 어떻게 해석해야하는지는 잘 모르겠음
- https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=gracestock_1&logNo=120200806864

 
![](https://i.imgur.com/JgzJNVH.png)

- 인간이 하는 추천에 대한 설명의 질이 우사성 기반 설명보다 더 높은 품질을 달성
- 설명의 질은 조건과 추천의 질뿐만 아리날 조건과 사회적 존재 사이의 매개자 역할을 한다.
- 조건은 추천 품질에 부정적인 직접적인 영향을 주고, buddy가 낮은 품질의 추천을 제공한다.

