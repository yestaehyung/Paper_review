
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
- alpaca
	- https://github.com/tatsu-lab/stanford_alpaca
- koalpaca
	- https://github.com/Beomi/KoAlpaca
- alpaca-lora
- dolly
- dalaiLlama
- wizardLM
# llama 공부

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
- llama 7B 모델을 frozen 하고 1.2

성능 기준표
- https://tatsu-lab.github.io/alpaca_eval/


https://github.com/shawwn/llama-dl

사람의 knowledge에서 온 attribute를 잘 이야기해야할 것 같다.    
무조건 벤치마크 하면 좋을 것 같다       

# AutoGPT

AutoGPT
- https://github.com/Significant-Gravitas/Auto-
- https://www.youtube.com/watch?v=CHzNNxZOIYI&t=15s
- 경쟁사 분석 시킬 수 있을 듯

카드 사용할 수 있게 되면 결제해서 사용하는 것이 좋을 듯 함


# Langchain

LangChain
- 용량이 큰 문서를 쪼개는 역할을 한다. 
- Fashion 정보가 담겨있는 책을 LangChain으로 모두 chunk화 하고 chatgpt에게 물어볼 때 같이 정보를 넘긴다. 
