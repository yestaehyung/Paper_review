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