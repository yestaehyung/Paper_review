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