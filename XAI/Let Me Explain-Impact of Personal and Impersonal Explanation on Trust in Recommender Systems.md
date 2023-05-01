실험 중심으로 H에게 업데이트

중요하다고 생각되는 부분 붙여넣기

ABSTRCT
Consequently, we suggest that RS should provide richer explanations in order to increase their perceived recommendation quality and trustworthiness.

INTRODUCTION


현 추천 시스템의 상황

Even though recommendation algorithms have become highly accurate in terms of estimating a user’s preferences [1, 15], they oftentimes appear as “black boxes” by concealing important details from their users. As a consequence, users create an unfitting mental model of the RS which may result in distrust and ultimately even in rejection of the system’s recommendations [17, 46].

RS are faceless entities lacking the human properties that are important for the development of trust, thus making it difficult for users to form bonds of any kind.

이전 연구에서 어떻게 추천 시스템을 설명하려는 노력에 대한 방법

One way to alleviate this, is to introduce social components into RS [6, 26]. There is a growing number of websites where automated and human-generated recommendations are combined—the latter, for example, in form of customer product reviews. For the reasons above, personal recommendation sources, i.e. users providing recommendations, are often associated with a higher trustworthiness [26, 44].

In the same line, designers of RS often strive to increase transparency and trustworthiness by providing textual ex- planatory components for recommendations [5, 46, 50]. A very common technique is to indicate similarity between re- commendations and items the user is currently browsing or has expressed preferences for in the past. A well-known ex- ample for the former is Amazon’s “Users who bought . . . also bought . . . ” explanation. Similar kinds of explanations are applied by, for instance, Netflix and Spotify. Even though the effectiveness of such simplistic approaches utilizing similarity- based explanations has been questioned [5, 12], 


이전 추천 시스템에서의 설명 하는 것의 문제점

a thorough empirical comparison with systems using richer explanations— especially in terms of the perceived trustworthiness and its influential factors—is still missing.

이 논문에서 저자들이 주장하는 것
- 지나치게 단순한 설명이 추천 소스에 대한 신뢰를 확립하는데 관련한 표현력과 사회적 특성이 부족하다?
	- 이 주장을 뒷받침하기 위해 user study를 수행함
		- 참가자들이 다른 사람이나 일반적인 RS에 의해 선택된 권장사항을 평가하도록 하는 study
		- 추천 결과에는 RS에 대한 개인적인 조건 또는 유사성 기반에 대한 설명이 구성되어 있음
	- By utilizing tools of causal statistical inference, i.e. structural equation modeling [33] and the counterfactual framework [18, 35, 40] -> 이걸 수행해서 충분한 설명이 신뢰 구축 과정에 큰 역할을 한다는 것을 확인하였다. 
결과적으로 인간이 정보를 교환하는 방식을 모방하는 설명할 수 있는 컴포넌트를 RS 개바 더하는 것은 