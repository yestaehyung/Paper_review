
# 최신 기술
최신 기술들  (6월 기준 아님!!!!!)     
- GPT4ALL
	- https://gpt4all.io/index.html
- llama
	- https://github.com/facebookresearch/llama
	- https://github.com/juncongmoo/pyllama
- llama-adapter
	- https://github.com/OpenGVLab/LLaMA-Adapter
- vicuna
	- https://github.com/lm-sys/FastChat
- StableVicuna
	- 13B 모델에서 가장 잘 돌아가는 것 같음
- alpaca
	- https://github.com/tatsu-lab/stanford_alpaca
- koalpaca
	- https://github.com/Beomi/KoAlpaca
- alpaca-lora
- dolly
- dalaiLlama
- wizardLM
	- 7B 모델이 가장 잘 작동하는 것 같음
- MPT
	- 상업용으로 사용이 가능함

transformer agent
- Langchain을 사용하기 쉽게 만든 것 같음


# llama

라마 유료 강의: https://fastcampus.co.kr/data_online_llama
https://github.com/facebookresearch/llama

temperature -> 높으면 창의적인 대답, (logit / temperature) -> 이렇게 code 상에 구성이 되어있다. 
top p -> 높으면 정확한 것을 위주로

params.json -> 모델의 정보를 담고 있는 json 파일, 차원이 어떻게 되고, head 어떻게 되고, layer가 어떻게 되는지 

sentencepiece -> 라이브러리 사용해서 tokenizer 를 만들게 된다.


Image feature 추천
- LLama-adapter v2 multimodal를 사용해서 추천 결과를 설명한다.
Attribute feature 추천
- attribute 결과를 사용해서 추천을 한다. 

**양자화 (Quantization)**
- 부동소수점으로 표현되는 파라미터들을 특정 비트 수로 줄이는 방법

상업적으로 사용가능한 것
- https://well-chauffeur-a16.notion.site/LLM-d23b30bc16c34c03b55185dcda442eae

llama-adapter
- https://arxiv.org/pdf/2303.16199.pdf
- llama 7B 모델을 frozen 하고 1.2M의 파라미터만 학습한다. A100 8개로 1시간 만에 fine-tuning이 가능하다. 
- FLAN 이라는 모델은 instruction tuning method를 소개함, non-tuned LLM을 unseen task에서 수행 가능하게 하는 방법
- PromptSource는 web-based GUI의 개발 환경을 제공
- InstructGPT는 instruction following power를 증명한 논문인데, GPT-3.5와 GPT-4의 성능을 따라 잡을 수 있었음 

성능 기준표
- https://tatsu-lab.github.io/alpaca_eval/


https://github.com/shawwn/llama-dl

사람의 knowledge에서 온 attribute를 잘 이야기해야할 것 같다.    
무조건 벤치마크 하면 좋을 것 같다       

# Alpaca

175개의 사람이 작성한 질문-답변 fair에서 GPT-3.5를 활용하여 52K의 학습 데이터로 확장하여 활용   
-> GPT-3.5의 결과를 따라해서 성능을 비슷하게 만들어 버린다...    

llama-7b를 fin-tuning 해서 gpt-3.5와 비슷한 성능이 날 수 있도록 함    

# InstructGPT

GPT-3를 사람이 직접 작성한 질문/대답의 데이터셋으로 추가학습을 한 것     

2022년도 포스팅 보고 정리함    
- RLHF (reinforcement learning with human feedback)이 적용됨
	- 1. GPT-3가 주어진 지시문대로 행동하도록 가르치기 위해


# Vicuna

ShareGPT의 데이터를 사용, 사람이 질문하면 GPT가 답변한 내용을 공유하는 사이트


# WizardLM

ChatGPT를 써서 자동으로 데이터셋을 생성, Evol-Instruct를 사용하였는데, self-instruct보다 복잡한 데이터를 생성할 수 있음

# AutoGPT

AutoGPT
- https://github.com/Significant-Gravitas/Auto-
- https://www.youtube.com/watch?v=CHzNNxZOIYI&t=15s
- 경쟁사 분석 시킬 수 있을 듯

카드 사용할 수 있게 되면 결제해서 사용하는 것이 좋을 듯 함


# Langchain

LangChain
- 다양한 prompt, model을 사용하기 쉽게 만들어 주는 역할을 한다. 
- 용량이 큰 문서를 쪼개는 역할을 한다. 
- Fashion 정보가 담겨있는 책을 LangChain으로 모두 chunk화 하고 chatgpt에게 물어볼 때 같이 정보를 넘긴다. 


# LoRA
## 배경
- GPT-3는 Over-parametrized model 이다.
- 모델이 학습한 일부의 정보만 가지고 와서 downstream에 사용한다.


- 데이터셋을 어떻게 구성을 할 것인가?
-  LLM이 하려는 목적이 무엇인지?
	- 노이즈를 제거하고, 부족한 정보를 채워줄수 있는 파인튜닝 모델이 필요
- ChatGPT에게 질문을 해서 JSON을 구성한다.
- In context learning vs fine-tuning


# Survey

- PLM과 LLM의 차이 -> LLM이 더 큰 모델,
-  잘 수행되는 Instruct GPT [61] 및 Alpaca [124]는 Flan 시리즈 LLM [62, 64]보다 더 적지만 더 다양한 명령(또는 인스턴스)을 활용하기 때문에 인스턴스 수 [253]보다 명령의 다양성과 품질이 더 중요한 것으로 보입니다.
- Large Language Models Encode Clinical Knowledge
- https://github.com/tatsu-lab/stanford_alpaca#fine-tuning
- In context learning
	- A survey for in-context learning
	- ![](https://i.imgur.com/hSQHvSz.png)
## ICL vs fine-tuning?? 

![](https://i.imgur.com/oy0wN8F.png)


https://github.com/BradyFU/Awesome-Multimodal-Large-Language-Models

Instruction tuning 을 하는 것이 가능할까?

내가 하려고 하는 것

제품 명을 받았을 때  => 적당한 길이의 상세 설명으로 바꾸어 주는 것
적당한 길이의 상세 설명에 이상한 정보가 포함되는 것 -> noise

우선 파인튜닝을 하면 이 task를 잘한다는 것을 확인함, 그런데 생성한 설명의 정확도는 보증하지는 못함
-> 어떻게 더 정확한 정보를 생성하게할 수 있을 것인지??
-> 패션 정보를 알려준다?

파인튜닝에 사용하는 프롬프트를 다양하게..? -> 그러면 instruction tuning이 더 좋은 건 아닌건지?

https://www.sktenterprise.com/bizInsight/blogDetail/dev/4222