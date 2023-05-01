일단 중요하다고 생각되는 부분 가지고 오기

ABSTRACT

We argue that explanations must be more re- latable to other concepts, hypotheticals, and associations. Inspired by the perceptual process from cognitive psychology, we propose the XAI Perceptual Processing Framework and RexNet model for relatable explainable AI with Contrastive Saliency, Counterfactual Synthetic, and Contrastive Cues explanations.

Introduction

이전 연구 흐름
their complexity limits their use in real-world applications due to the difficulty to understand them [31]. To address this, much research has been conducted on explainable AI (XAI) to develop new XAI algorithms and techniques [3, 7, 30, 36], understand user needs [22, 58, 59, 72, 104] and evaluate their helpfulness [2, 11, 12, 18, 21, 64, 83, 105].


문제 상황

Despite the myriad XAI techniques, many of them remain difficult to understand, due to the lack of human-centered design that do not satisfy human needs [23, 72, 104]. Miller identified contrastive reasoning as a particular reason that people ask for explanations [72] — "one does not explain events per se, but that one explains why the puzzling event occurred in the target cases but not in some counterfactual contrast case." [35]. We further argue that explanations lack relatability towards concepts that people are familiar with, and therefore they seem too low-level technical and not semantically meaningful. Existing contrastive explanation techniques [20, 54, 73, 102] remain unrelatable, hence limiting their interpretability

이 논문에서 하려는 것

In this work, we extend the framing of relatable explanations beyond contrastive explanations to include saliency, counterfactuals, and cues. Explanations should be relatable towards concepts via contrastive explanations, towards exemplars by pro- viding counterfactual examples, and towards associated auxiliary concepts such as sensory and semantic cues.

1.  XAI Perceptual Processing Framework for relatable explanations inspired from theories in human cognition.
2.  RexNet model with multiple relatable explanation (Contrastive Saliency, Counterfactual Synthetic, Contrastive Cues).
3.  First to provide relatable explanations for audio predictions.
4.  Evaluation of usage and usefulness of relatable explanations.

Counterfactual Explanation
- 반사실적 설명
- X 가 발생하지 않았더라면 Y가 발생하지 않았을 것 이라는 형태로 인과관계를 설명
	- 내가 뜨거운 커피를 한 모금 마시지 않았더라면 혀가 데이지 않았을 텐데
- 해석 가능한 머신러닝에서는 반사실적 설명이 개별 인스턴스의 예측에 대한 설명으로 사용된다.
- '사건'은 인스턴스의 예측된 결과값이고, '원인'은 모델의 입력값으로 사용되어 특정 결과를 '유도'한 인스턴스의 특성값
- 우리는 모델의 입력값을 예측의 원인으로 생각한다.
- 반사실적 설명은 예측값을 사전 정의된 결과값으로 변경하는 특성값의 작은 변화를 설명

Contrastive Saliency
- Saliency detection -> 관심있는 물체를 관심이 없는 것으로부터 분리시키는 것

Counterfactual Synthetic
- StarGan을 확장해서 음성데이터에 활용가능한 StarGan-VC를 통해 counterfactual synthetic 을 생성함


Contrastive Cues


2.1 Explainable AI techniques

Much research has been done to develop explainable AI (XAI) for improving model transparency and trustworthiness. An in- tuitive approach is to point out which features are most impor- tant. Attribution explanations do this by identifying importance using gradients [99], ablation [92], activations [97], or decomposi- tions [8, 75, 90]. In computer vision, attributions take the form of saliency maps (e.g., [97]). Explaining by referring to key examples is another popular approach. This includes simply providing arbitrary samples of specific classes, cluster prototypes or criticisms [46], or influential training set instances [49]. However, users typically have expectations and goals when asking for explanations.

Users ask for contrastive explanations when expected outcomes do not happen. A simple answer would find the attribution differ- ences between the actual (fact) and expected (foil) outcomes [84] However, this is naive because users are truly asking for what differences in feature values, not attributions, would lead to the alternative outcome. That is a counterfactual explanation. Further- more, to anticipate a future outcome or prevent an undesirable one, users could ask for counterfactual explanations. Indeed, contrastive explanations are often conflated with counterfactual explanations in the research literature. Such explanations suggest the minimum changes in the current case to achieve the desired outcome [103]. Trained decision structures, such as local foil trees [102], Bayesian rule lists [55], or structural causal models [73] can also serve as counterfactual explanations. Though typically explained in terms of feature values [20, 54, 103] or anchor rules [91], techniques have been developed to synthesize counterfactuals of unstructured data (e.g., images [29] and text [33]). In this work, we employ the syn- thesis approach to generate counterfactuals of audio data.

There are many explanation types and Lim and Dey have framed them in an intelligibility taxonomy as Why (Attribution), Why Not (Contrastive), and How To (Counterfactual) [59]. Many of these XAI techniques have been independently developed or tested, so their usage is disparate. In this work, we unify them in a common framework and integrate them in a single machine learning model.

2.2 Human-Centered Explainable AI

Abdul et al. [1] found a large gap between XAI algorithms and human-centered research. To close this gap, HCI researchers have been active in evaluating the various benefits of XAI or lack thereof, including understanding and trust [64], uncertainty [62, 105, 110], cognitive load [2], types of examples [11], etc. Studies have sought to determine the "best" explanation type [64, 100], but others have revealed the benefit of reasoning with multiple explanations [6, 61, 63]. Hence, we propose a unified framework to provide multiple relatable explanations together. We determined our human-centered explanation requirements by studying literature on human cognition, which is epistemologically similar to works grounded in philosophy and psychology [72, 104], and unlike empirical approaches to elicit user requirements [22, 58, 59]. Furthermore, current works focus on explaining higher-level reasoning tasks, but not perception tasks that are commonplace. This has implications on the depth of explanations to provide, which we investigate in this work.