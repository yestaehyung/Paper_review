---
title: "LLM 성능 향상 방법"
source: "https://chatgpt.com/c/67f32144-d55c-800a-830b-7b9ef6f821a9"
author:
  - "[[ChatGPT]]"
published:
created: 2025-04-07
description: "ChatGPT conversation with 10 turns"
tags:
  - "clippings"
---
## ChatGPT

LLM에게 특정 무언가를 refine 하여 정확도나, 성공률 같은 지표를 향상시키는 방법론이나 이것을 활용한 논문을 찾을 수 있을까?

---

## ChatGPT

LLM의 어떤 측면을 refine하고자 하시는 건가요? 예를 들어 특정 태스크의 성능(예: 요약, 번역, 질의응답), 도메인 적합성, 추론 능력 향상 등 어떤 측면의 정확도나 성공률을 높이고 싶으신지 알려주시면 관련된 방법론이나 논문을 더 정확하게 찾아드릴 수 있어요.

---

## ChatGPT

LLM이 생성한 것에 대해서 refine 하는 것을 찾고 싶어, LLM을 개선하는 것이 아니야 예를 들어서 프로필을 만든다고 하면, LLM이 생성한 프로필에 대해, LLM이 프로필을 다시 보고 이게 정말 맞는 것인지 개선하는 거지 LLM은 chatgpt와 같으거면 좋을 것 같고, 최신 뉴립스 논문이면 좋을 것 같아

---

## ChatGPT

좋아요. NeurIPS(뉴립스) 최신 논문 중에서, ChatGPT나 유사한 LLM이 생성한 아웃풋(예: 프로필, 설명 등)을 다시 검토하고 개선(refinement)하여 정확도나 성공률을 높이는 방법론에 관한 연구를 찾아볼게요. 논문에는 가능한 한 구체적인 방법과 정량적 지표 향상 결과가 포함된 것을 우선할게요. 조금만 기다려 주세요, 곧 결과를 정리해서 알려드릴게요.

## Refinement Methods for Improving LLM Outputs (NeurIPS 2023–2024)

The table below summarizes several recent research papers (mostly NeurIPS) that propose **refinement approaches** for LLM-generated outputs, along with their methods and performance gains:

| **Paper** | **Authors (Year)** | **Refinement Approach** | **Key Outcomes** |
| --- | --- | --- | --- |
| **Self-Refine: Iterative Refinement with Self-Feedback** | Aman Madaan *et al.* (NeurIPS 2023) | Uses the same LLM to generate an initial output, then have the LLM itself provide feedback on that output and iteratively refine it – all at test-time, with no additional training or supervised data required [^1]. | Across 7 diverse tasks (dialog generation, math reasoning, etc.), this method improved performance by **~20% (absolute)** on average over one-shot generation, with refined outputs preferred by both automatic metrics and human evaluators [^2]. |
| **Reflexion: Language Agents with Verbal Reinforcement Learning** | Noah Shinn *et al.* (NeurIPS 2023) | Introduces *Reflexion*, where an agent doesn’t update its weights but **verbally self-reflects** on feedback. The LLM agent converts feedback signals (e.g. error messages or critique) into a textual reflection stored in memory, and conditions future outputs on this memory to iteratively improve decisions [^3]. | Achieved **significant improvements** across reasoning, decision-making, and coding tasks. For example, on the HumanEval code benchmark it reached **91% pass@1 accuracy**, outperforming GPT-4 (which achieved ~80%) [^4]. |
| **LeDex: Training LLMs to Better Self-Debug and Explain Code** | Nan Jiang *et al.* (NeurIPS 2024) | Proposes a training framework for code generation where the model **iteratively debugs its code**. LeDex automatically builds a dataset of code “explanations and refinements” by generating multiple explanation-and-fix trajectories (using the LLM itself or a larger teacher) and filtering them via execution results [^5]. The model is then fine-tuned on these successful and failed refinement trajectories (with a specially designed reward for good explanations and fixes), and further optimized with RL. | This approach markedly improved code correctness: supervised fine-tuning alone boosted the code pass@1 rate by up to **+15.9%** (and pass@10 by +9.3%) across several benchmarks, and an additional RL fine-tuning stage added up to **+3.5%** more on pass@1 (and +2.5% on pass@10) [^6]. The resulting LLM can continuously refine its code and produces more helpful explanations of bugs (as confirmed by human evaluation) [^6]. |
| **SLED: Self Logits Evolution Decoding for Improving Factuality in LLMs** | Jianyi Zhang *et al.* (NeurIPS 2024) | Introduces a novel **decoding-time refinement** method to improve factual accuracy. SLED leverages the model’s *latent knowledge* by contrasting the final-layer output logits with the logits from earlier transformer layers, and then applying an approximate gradient-based adjustment to **self-refine** the output in real-time [^7]. This guides the generation to be more consistent with facts the model *does* know internally, without any external knowledge or fine-tuning. | **Consistently improves factual accuracy** (truthfulness of outputs) by up to **20%** compared to standard decoding methods, while maintaining fluent language quality [^8]. Notably, SLED operates with negligible added latency and can be combined with other decoding strategies for further gains [^8]. |
| **Toward Self-Improvement of LLMs via Imagination, Searching, and Criticizing (AlphaLLM)** | Ye Tian *et al.* (NeurIPS 2024) | Proposes **AlphaLLM**, which integrates a Monte Carlo Tree Search (MCTS) loop with an LLM for complex reasoning tasks. The LLM “imagines” possible solution steps, uses MCTS to **search** multiple reasoning trajectories, and employs a set of critic models to **critique** and score these trajectories [^9]. High-scoring solutions are then used to update the LLM’s own responses (in a self-improvement loop) – all without additional human-provided annotations. | Demonstrated **substantial performance gains** on mathematical reasoning benchmarks. For instance, starting from a strong 70B model (~73.7% accuracy on GSM8K math problems), AlphaLLM’s search-and-refine loop boosted accuracy to **88.9%**, and after two self-improvement iterations it reached **~92%**, **rivaling GPT-4’s performance** on the same task [^10]. Similar improvements were observed on other math tasks (e.g. more than doubling accuracy on the MATH dataset) [^10]. |
| **Code Repair with LLMs Gives an Exploration-Exploitation Tradeoff (REx)** | Hao Tang *et al.* (NeurIPS 2024) | Focuses on **iterative code refinement** using feedback from test cases. The authors frame the process as a **bandit problem**: at each step, the algorithm must decide whether to *exploit* the current best partial solution or *explore* a different solution path [^11]. They introduce **REx**, which uses Thompson Sampling to adaptively choose which generated program to refine next, rather than always picking the last or best one. This balances exploration vs. exploitation in the refinement search tree of code edits. | REx solves **more programming problems with fewer LLM calls** compared to greedy or breadth-first refinement strategies [^12]. It achieved new **state-of-the-art results** in several challenging code generation domains (such as loop invariant synthesis, visual reasoning puzzles, and competition-level programming tasks) [^13], indicating a more efficient and effective refinement strategy. |
| **LLM Self-Correction with DeCRIM (Decompose, Critique, and Refine)** | Thomas P. Ferraz *et al.* (NeurIPS 2024 Workshop) | Targets **instruction-following with multiple constraints** (e.g. “write a post in a *funny* tone *without* using hashtags”). The DeCRIM pipeline first **decomposes** a complex instruction into a checklist of individual constraints. A separate *Critic* model then evaluates the LLM’s output to see if any constraint is violated and pinpoints where [^14]. The LLM subsequently attempts to **refine** its answer to fix those specific issues, iterating as needed. | On the new RealInstruct benchmark of real user queries with multiple constraints, DeCRIM boosted an open-source model’s success rate by **+7.3%** (and by +8.0% on a related IFEval benchmark) even with only weak automated feedback [^15]. With stronger feedback signals, a DeCRIM-augmented LLM was able to **exceed GPT-4’s performance** on following complex constrained instructions [^15], substantially closing the gap between open models and proprietary ones in this setting. |

---

## ChatGPT

근데 이런 방법론을 사용자의 프로필을 생성할 때 어떻게 사용할 수 있을까

---

## ChatGPT

사용자 프로필을 생성할 때 위의 논문들에서 사용된 **refinement(개선)** 방법론을 실제로 어떻게 적용할 수 있는지에 대해 구체적으로 설명해 드릴게요.

---

## 📌 1. Self-Refine (자기 피드백을 통한 프로필 정제)

- **방법론:**
	- LLM이 초기에 사용자의 리뷰나 행동 데이터를 기반으로 프로필 초안을 생성.
	- 동일한 LLM에게 생성된 프로필을 다시 입력으로 주고, 스스로에게 "이 프로필이 사용자의 특성을 충분히 반영하는가?" 등 자기 비판적 질문을 던지게 함.
	- 이 피드백을 바탕으로 프로필을 단계적으로 refine.
- **예시 시나리오:**
	```
	rustInitial Profile: 
	"User prefers outdoor activities, enjoys hiking, and seeks quiet environments."Self-Refinement Prompt:
	"Review the above profile critically. Could this profile better reflect the user's implicit personality or social preferences found in their reviews?"
	Refined Profile:
	"User prefers outdoor activities and values solitude during leisure, often emphasizing tranquility. Additionally, shows subtle interest in community-oriented events that involve outdoor group activities."
	```
- **장점:**
	- 프로필의 정확도 향상, 숨겨진(implicit) 속성을 추가로 발견 가능.

---

## 📌 2. Reflexion (반성적 피드백을 통한 반복적 개선)

- **방법론:**
	- LLM이 생성한 프로필의 한계나 문제점을 식별하는 “반성적(reflective)” 문장을 LLM이 스스로 작성하여 메모리에 저장.
	- 이후 프로필을 업데이트할 때마다 메모리에 저장된 반성적 피드백을 고려하여 반복적으로 프로필을 개선.
- **예시 시나리오:**
	```
	javaInitial Profile: 
	"User is enthusiastic about local food scenes and culinary tourism."
	Reflection Feedback(LLM 자체 생성):
	"이 프로필은 사용자의 사회적 특성을 충분히 담지 못했고, 미식 관련 리뷰에서 나타난 타인과의 소통을 선호하는 사회적 특성이 반영되지 않았음."
	Improved Profile:
	"User is enthusiastic about local culinary experiences, enjoys social dining contexts, and values interactions with local chefs and fellow travelers."
	```
- **장점:**
	- 사용자 프로필이 더욱 다차원적이고 사회적 특성을 포함할 수 있음.

---

## 📌 3. SLED (내부 지식 대비를 통한 정확성 향상)

- **방법론:**
	- LLM이 특정 사용자에 대한 프로필을 생성할 때, 최상위 레이어에서 출력된 결과(logits)를 중간 레이어의 정보(logits)와 비교하여 일관되지 않은 부분을 자체적으로 식별하고 수정하여 보다 정확한 프로필 생성.
- **예시 시나리오:**
	```
	sqlInitial Profile: 
	"User loves luxury travel and high-end restaurants."
	내부 지식 대비 (LLM 중간층 분석):
	"중간층에서 발견된 사용자의 선호 데이터는 높은 소비 성향보다는 현지의 소박한 경험을 더 선호하는 경향이 있음."
	Refined Profile:
	"User enjoys authentic local experiences and appreciates restaurants offering genuine local cuisine rather than high-end establishments."
	```
- **장점:**
	- 사용자의 실제 데이터와 내부적으로 일관된 프로필 생성 가능.

---

## 📌 4. DeCRIM (복잡한 지침 분해 및 조건 확인을 통한 프로필 개선)

- **방법론:**
	- 사용자 프로필 생성 시 만족해야 하는 조건(예: personality, social traits, explicit preferences)을 별도 항목으로 분리하고, 각 조건을 LLM이 개별적으로 평가하여 충족 여부를 판단하고 수정하는 방식.
- **예시 시나리오:**
	```
	javaInitial Profile:
	"User enjoys nightlife."
	Decomposition & Critique:
	- Explicit preference(nightlife): ✔️
	- Personality trait(extraversion): ❌ 부족
	- Social trait(group interactions): ❌ 명확하지 않음
	Refined Profile:
	"User enjoys nightlife, showing clear extraversion by actively engaging in large-group social gatherings and vibrant social scenes."
	```
- **장점:**
	- 프로필의 완성도와 조건 충족 여부가 명확해짐.

---

## 📌 5. AlphaLLM / REx (탐색과 평가를 통한 최적의 프로필 찾기)

- **방법론:**
	- 프로필 생성 시 여러 후보 프로필을 탐색한 후, 각 프로필의 정확성이나 만족도를 평가하여 최적의 프로필을 찾고 반복적으로 개선.
- **예시 시나리오:**
	```
	vbnetGenerated candidate profiles:
	A:"User prefers adventure tourism and nature photography."B:"User prefers cultural experiences and city exploration."
	평가(LLM이 자체 평가 수행):
	- A는 사용자의 리뷰 데이터에 더 정확히 부합함 (점수 0.85)
	- B는 부분적으로만 일치 (점수 0.55)
	최적의 프로필 선택 및 개선:
	"User prefers adventure tourism, actively engages in nature photography, and shows secondary interest in exploring local cultures in rural regions."
	```
- **장점:**
	- 프로필 정확도와 적합도를 최대화할 수 있음.

---

## ✅ 각 방법의 활용성 평가 및 추천

| 방법론 | 주요 강점 | 권장 활용 상황 |
| --- | --- | --- |
| Self-Refine | 데이터 부족 상황에서도 성능 향상 | 명확한 데이터 부족 시 |
| Reflexion | 복잡한 특성을 심층적으로 발견 가능 | personality/social trait 등 복합적 특성 |
| SLED | 내부 지식 기반 신뢰성 향상 | 프로필 정확성이 특히 중요한 경우 |
| DeCRIM | 조건 충족 여부를 정확히 확인 가능 | 명확한 프로필 생성 기준이 있을 때 |
| AlphaLLM / REx | 탐색적 접근으로 최적 프로필 발굴 가능 | 많은 후보 중 최적 프로필을 찾아야 할 때 |

---

이러한 최신 논문들의 refinement 접근법은 사용자의 프로필 정확도와 성공률을 효과적으로 높일 수 있는 유망한 방법입니다. 사용자의 데이터 특성, 프로필의 복잡성 및 정확도 기준에 따라 가장 적합한 접근법을 선택하여 활용하면 됩니다.

---

## ChatGPT

1번과 2번에 대해서 더 구체적인 시나리오를 생각해 볼까? 사용자 프로필을 암시적 선호도, 성격, 활동성 이 세가지로 구성한다고 할 때 어떻게 하는게 좋을까?

---

## ChatGPT

좋습니다. 아래에 말씀하신 세 가지 구성요소( **암시적 선호도, 성격, 활동성** )를 중심으로,  
위에서 소개한 두 가지 접근법( **Self-Refine** 과 **Reflexion** )을 프로필 생성에 보다 구체적으로 적용하는 시나리오를 만들어 드리겠습니다.

---

## 📝 기본 전제

- **생성할 프로필의 구성 요소**:
	- **암시적 선호도 (Implicit Preferences)**: 사용자의 리뷰나 행동에 드러나진 않았으나 추론 가능한 선호.
	- **성격 (Personality)**: 사용자의 성격적 특성 (외향성, 성실성 등).
	- **활동성 (Activity Level)**: 활동적이거나 정적인 라이프 스타일 여부.
- **데이터**: 사용자가 남긴 리뷰 데이터 (호텔, 식당 등에서의 리뷰).

---

## 🎯 \[1번 방법론\] Self-Refine을 활용한 프로필 생성 시나리오

### Step 1. 초기 프로필 생성 (LLM의 1차 출력)

- **입력**:
	```
	text다음은 사용자 A의 TripAdvisor 리뷰 10개입니다. 
	이 리뷰들에서 나타나는 사용자의 암시적 선호도, 성격, 활동성에 대한 간단한 프로필을 만들어 주세요.
	```
- **초기 프로필 예시**:
	```
	diff- 암시적 선호도: 로컬 음식점과 카페를 선호함.- 성격: 조용하고 내향적인 성향을 보임.- 활동성: 다소 정적인 편임.
	```

---

### Step 2. Self-Refinement (스스로 피드백)

- **입력**:
	```
	text방금 생성된 사용자 A의 프로필을 다시 읽고, 
	리뷰 데이터에서 놓친 중요한 암시적 선호도, 성격, 활동성 관련 특성이 없는지 스스로 점검해 주세요.
	부족하거나 잘못된 점을 명확하게 지적하고, 그 이유를 설명하세요.
	```
- **LLM의 자기 평가 예시**:
	```
	bash위 프로필은 사용자의 암시적 선호도를 '로컬 음식점과 카페 선호'로 제한했으나, 
	실제 리뷰 데이터에는 자연환경이 좋은 숙소나 공원에 대한 긍정적 평가가 다수 포함되어 있음. 따라서 사용자는 자연 친화적인 장소에 대한 암시적 선호도도 가지고 있다고 볼 수 있음.
	성격 부분은 내향적이라고만 하였으나, 몇몇 리뷰에서 낯선 사람과의 짧은 상호작용에 긍정적 평가를 보인 것을 볼 때, 사용자는 상황에 따라 제한된 범위에서 외향적 특성도 발휘하는 것으로 보임.
	활동성에 관해 ‘정적인 편’이라고만 하였으나, 리뷰 데이터를 보면 정적이지만 가끔 도보 투어나 도시 내 가벼운 산책과 같은 낮은 수준의 활동을 선호하는 경향이 발견됨.
	```

---

### Step 3. Refined 최종 프로필 생성 (개선)

- **입력**:
	```
	text위의 피드백을 기반으로 사용자 A의 프로필을 보다 정확하게 개선하여 다시 작성해 주세요.
	```
- **Refined 프로필 예시**:
	```
	diff- 암시적 선호도: 로컬 음식점과 카페를 선호하며, 자연 친화적이고 조용한 장소에서의 휴식을 중요하게 여김.- 성격: 기본적으로 내향적이나, 상황에 따라 제한된 사회적 상호작용을 즐기는 유연한 성격을 지님.- 활동성: 대체로 정적인 편이나 가벼운 산책이나 도보 투어 등 낮은 강도의 활동에는 관심이 있음.
	```

---

## 🎯 \[2번 방법론\] Reflexion을 활용한 프로필 생성 시나리오

### Step 1. 초기 프로필 생성

- **입력**: (동일)
- **초기 프로필 예시**:
	```
	diff- 암시적 선호도: 고급스러운 음식점과 호텔 선호.- 성격: 사교적이고 외향적.- 활동성: 매우 활동적임.
	```

---

### Step 2. Reflexion (자기 반성적 피드백 작성)

- **입력**:
	```
	text프로필과 원본 리뷰를 비교하여, 프로필이 원본 리뷰에서 드러난 정보와 얼마나 정확하게 일치하는지 스스로 평가해보세요.
	프로필이 리뷰와 일치하지 않는 부분에 대해서는 어떤 문제가 있는지 반성적 피드백(reflexion)을 작성하세요.
	```
- **Reflexion(반성적 피드백) 예시**:
	```
	bash- 암시적 선호도에 대해, '고급스러운 음식점과 호텔 선호'라고 하였지만 실제 리뷰들은 대부분 가격보다는 분위기와 음식의 현지성을 강조함. 따라서 프로필이 실제 선호와 다르게 과장됨.
	- 성격이 '사교적이고 외향적'이라 했으나, 리뷰에서 사용자 본인이 혼자 여행하는 것을 선호하고, 지나친 교류를 피하는 것이 명확히 드러남. 따라서 성격 부분은 명백히 잘못됨.
	- 활동성이 '매우 활동적'이라 평가되었지만, 리뷰 데이터에 따르면 사용자가 휴식과 느긋한 일정, 휴양형 숙박을 선호하는 정적 성향이 더 우세함.
	```

---

### Step 3. Reflexion을 고려한 프로필 재작성

- **입력**:
	```
	text작성된 reflexion을 토대로 프로필을 수정하여 더욱 정확하게 재작성하세요.
	```
- **Refined 프로필 예시**:
	```
	diff- 암시적 선호도: 현지 특색이 강한 음식점과 숙소의 분위기를 중시하고, 합리적인 가격대에서 경험을 즐기는 경향이 있음.- 성격: 내향적이며 혼자 여행하는 것을 선호하고, 불필요한 사교 활동은 피하는 편.- 활동성: 대체로 휴식 중심의 여행을 선호하며, 여유 있는 일정과 정적인 활동을 추구함.
	```

---

## 🎯 각 방법론의 장점 비교

| 방법론 | 장점 | 추천 상황 |
| --- | --- | --- |
| Self-Refine | 빠르게 피드백 생성, 단계별 개선 | 빠른 프로필 개선 필요 시 |
| Reflexion | 문제점의 근거를 구체적으로 제시 | 프로필 품질의 신뢰성이 특히 중요한 상황에서 추천 |

---

## 🧑💻 정리 및 추천

- 빠르고 단계적 개선이 필요하면 **Self-Refine** 추천
- 프로필 정확성과 신뢰성이 우선이라면 **Reflexion** 추천

이 두 방법은 프로필 생성에서 매우 효과적이며, 활용 목적과 상황에 따라 선택하면 됩니다.

---

## ChatGPT

이제 어떤 것인지 이해가 되었는데, refine에 사용하는 데이터에 대해서 이야기 해보자 나는 리뷰 데이터에서 프로필을 만드려고 하는데 어떤 형식으로 데이터가 있어야할까 프로필 만들 때는 어떻게 리뷰를 샘플링해서 사용할지, refine할 때는 어떤 식으로 샘플링 할지 논의해보자

---

## ChatGPT

좋습니다. 프로필 생성 및 refinement 단계에서 리뷰 데이터를 어떻게 준비하고 샘플링할지에 대해 체계적으로 논의해 볼게요.

---

## ✅ 1. 데이터의 형식

리뷰 데이터는 다음과 같은 형태를 갖추는 것이 프로필 생성에 적합합니다:

### 📌 필수 구성 요소:

- **사용자 ID** ( `user_id` )
- **리뷰 텍스트** ( `review_text` )
- **리뷰 시점** ( `timestamp` )
- **리뷰 대상의 카테고리** ( `category`: 호텔, 음식점 등)
- **리뷰 평점** ( `rating` )

### 📌 권장되는 데이터 예시:

```json
json[{"user_id":"user_001","review_text":"이 호텔은 매우 조용하고 자연 친화적이라 너무 좋았어요. 근처에 산책할 수 있는 공원도 있어요.","timestamp":"2024-02-10","category":"호텔","rating":5},{"user_id":"user_001","review_text":"현지인들이 자주 찾는 작은 카페였는데, 커피 맛도 좋고 편안했어요.","timestamp":"2024-01-05","category":"음식점","rating":4},
    ...
]
```

---

## ✅ 2. 프로필 생성을 위한 리뷰 샘플링 방법

프로필 생성을 위해서는 다음의 원칙을 따르는 것이 좋습니다:

### 📌 리뷰 개수

- 일반적으로 프로필 생성에 충분한 신뢰성을 확보하기 위해 **5~20개의 리뷰** 를 사용하는 것이 적절합니다.

### 📌 샘플링 방법 (초기 프로필 생성 시)

- **최신 리뷰 우선 방식** (최근 리뷰가 사용자의 현재 선호도를 가장 잘 반영)
- **다양성 기반 방식** (다양한 카테고리의 리뷰를 균형 있게 포함)
- **평점 기반 방식** (평점이 매우 높거나 낮은 리뷰를 우선적으로 포함해 극단적인 선호를 명확히 포착)

#### 추천 방법: 복합 샘플링 예시

- 최신 리뷰 50%, 카테고리 다양성 고려 30%, 극단적 평점(1~2점, 5점) 20%를 혼합하여 사용하는 것이 프로필의 균형성과 정확도를 높일 수 있습니다.

> **예시**: 리뷰 10개 샘플링 시
> 
> - 최신 리뷰 5개
> - 다양한 카테고리 리뷰 3개 (음식점 1개, 호텔 1개, 관광지 1개)
> - 평점 극단적 리뷰 2개

---

## ✅ 3. 프로필 Refine을 위한 리뷰 샘플링 방법

Refine 단계에서는 프로필이 충분히 정확한지 평가하거나, 잘못된 부분을 찾아야 하므로 샘플링 전략이 다소 달라집니다.

### 📌 Refinement 시 고려할 리뷰

- 초기 프로필 생성에 **사용되지 않은 리뷰** 를 반드시 포함  
	(이전 단계와 겹치지 않는 리뷰로 교차 검증 효과)
- 사용자의 **대표 성향을 잘 드러내는 리뷰** (강렬한 표현이나 특징적 문장을 가진 리뷰 포함)
- 프로필이 **잘못되었을 가능성이 있는 부분을 드러낼 리뷰** (초기 프로필과 충돌 가능성이 높은 리뷰 포함)

### 📌 추천 방법: 반대 사례 중심의 전략적 샘플링 예시

- 초기 프로필과 대조적(contradictory)일 수 있는 리뷰 위주로 40%
- 대표적이고 특징적인 리뷰 40%
- 임의(random) 리뷰 20%를 섞어서 일반화를 확인

> **예시**: 리뷰 5개로 refine 수행 시
> 
> - 프로필과 대조적인 리뷰 2개
> - 특징적이고 대표적인 리뷰 2개
> - 임의 리뷰 1개

---

## 📌 샘플링 전략을 프로필 생성-Refine에 적용한 예시 시나리오

### 🔸 초기 프로필 생성

| 선택 리뷰 기준 | 선택 리뷰 예시 |
| --- | --- |
| 최신 리뷰(50%) | 최근 5개 리뷰 |
| 다양한 카테고리(30%) | 호텔 리뷰 1개, 음식점 리뷰 1개, 관광지 리뷰 1개 |
| 극단적 평점(20%) | 평점 5점 리뷰 1개, 평점 1~2점 리뷰 1개 |

### 🔸 Refinement 프로필 검증 및 개선

| 선택 리뷰 기준 | 선택 리뷰 예시 |
| --- | --- |
| 초기 프로필과 대조적인 리뷰(40%) | 초기 프로필과 다른 특성을 보이는 리뷰 2개 |
| 대표적이고 특징적인 리뷰(40%) | 사용자의 성격이나 선호를 뚜렷하게 나타내는 리뷰 2개 |
| 임의(random) 리뷰(20%) | 무작위로 선택된 리뷰 1개 |

---

## ✅ 4. 프로필 생성과 refine에서 데이터 관리 시 주의사항

- 각 단계(생성 및 refine)에 사용된 리뷰 ID를 관리하여 중복 사용 방지
- 사용자마다 프로필 생성에 이용된 리뷰의 비율 및 수량을 기록하여 실험적 투명성 보장
- refine 후 프로필 정확도 향상 결과를 평가할 때는, 최초 프로필과 refine된 프로필의 정량적 비교를 명확히 할 수 있도록 샘플링 기준과 근거 리뷰를 명확히 기록할 것

---

## 🚩 요약 및 추천

| 단계 | 리뷰 개수 | 샘플링 전략의 요약 |
| --- | --- | --- |
| 초기 프로필 생성 | 5~20개 | 최신 리뷰 중심 + 카테고리 다양성 + 극단적 평점 혼합 |
| Refine(개선) | 3~10개 | 대조적인 리뷰 중심 + 대표 리뷰 + 랜덤 리뷰 |

이러한 데이터 형식과 샘플링 방법을 이용하면, LLM 기반의 프로필 생성 및 refine의 신뢰성과 정확성을 최대화할 수 있습니다.

[^1]: [nips.cc](https://nips.cc/virtual/2023/poster/71632#:~:text=text%2C%20we%20introduce%20Self,3.5) — text...

[^2]: [nips.cc](https://nips.cc/virtual/2023/poster/71632#:~:text=response%20generation%20to%20mathematical%20reasoning%2C,using%20our%20simple%2C%20standalone%20approach) — response generation to mathematical reasoning...

[^3]: [neurips.cc](https://neurips.cc/virtual/2023/poster/70114#:~:text=propose%20%5Cemph,making%20in) — propose \\emph...

[^4]: [neurips.cc](https://neurips.cc/virtual/2023/poster/70114#:~:text=match%20at%20L236%20language%20reasoning%29,methods%2C%20and%20agent%20types%2C%20and) — match at L236 language reasoning)...

[^5]: [neurips.cc](https://neurips.cc/virtual/2024/poster/94367#:~:text=open,and%20failure%20trajectories%20with%20a) — open...

[^6]: [neurips.cc](https://neurips.cc/virtual/2024/poster/94367#:~:text=reinforcement%20learning%20,understand%20bugs%20in%20source%20code) — reinforcement learning...

[^7]: [proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2024/hash/0939f13ffce3ff487509d902ddba4571-Abstract-Conference.html#:~:text=this%2C%20we%20introduce%20Self%20Logits,LLaMA%202%2C%20LLaMA) — this...

[^8]: [proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2024/hash/0939f13ffce3ff487509d902ddba4571-Abstract-Conference.html#:~:text=configurations%20such%20as%20the%20mixture,fluency%20and%20negligible%20latency%20overhead) — configurations such as the mixture...

[^9]: [proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5e5853f35164e434015716a8c2a66543-Abstract-Conference.html#:~:text=employing%20strategies%20that%20allow%20LLMs,language%20tasks%2C%20and%20the%20subjective) — employing strategies that allow LLMs...

[^10]: [proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2024/file/5e5853f35164e434015716a8c2a66543-Paper-Conference.pdf#:~:text=imagination,solving%20tasks%20in%20a) — imagination...

[^11]: [haotang1995.github.io](https://haotang1995.github.io/projects/rex#:~:text=iteratively%20refine%20code%2C%20with%20prior,solve%20more%20problems%20using%20fewer) — iteratively refine code...

[^12]: [haotang1995.github.io](https://haotang1995.github.io/projects/rex#:~:text=acquiring%20bandit%20problem%2C%20which%20we,using%20fewer%20language%20model%20calls) — acquiring bandit problem...

[^13]: [haotang1995.github.io](https://haotang1995.github.io/projects/rex#:~:text=Image%20REx%20established%20new%20state,three%20challenging%20code%20generation%20domains) — Image REx established new state...

[^14]: [neurips.cc](https://neurips.cc/virtual/2024/104307#:~:text=and%20proprietary%20models%2C%20we%20propose,3) — and proprietary models...

[^15]: [neurips.cc](https://neurips.cc/virtual/2024/104307#:~:text=DeCRIM%20works%20by%20decomposing%20the,4%20on%20both%20benchmarks) — DeCRIM works by decomposing the...