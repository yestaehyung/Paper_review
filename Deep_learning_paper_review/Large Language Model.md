
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

llama-a

성능 기준표
- https://tatsu-lab.github.io/alpaca_eval/


WSDM에서 사용하는 데이터랑 우리가 사용하는 데이터가 유사하다는 것을 확인해야한다. 
이쪽 도메인에서 많이 쓰이는 모델(성능비교) 다 가지고 온다, 

결국에 비교 데이터셋이 짧은 데이터셋인데, llama를 써서 aug된걸 넣게 되면, 원래 짧은 텍스트를 잘 예측하게 되야하는데 이게 잘 될지 의문이 있다.      

효과성을 보이는데 있어서 어떤 데이터를 택할 것인가가 중요하다.        

사람의 knowledge에서 온 attribute를 잘 이야기해야할 것 같다.    
무조건 벤치마크 하면 좋을 것 같다       

# AutoGPT

AutoGPT
- https://github.com/Significant-Gravitas/Auto-
- https://www.youtube.com/watch?v=CHzNNxZOIYI&t=15s
- 경쟁사 분석 시킬 수 있을 듯


# Langchain

LangChain
- 용량이 큰 문서를 쪼개는 역할을 한다. 
- Fashion 정보가 담겨있는 책을 LangChain으로 모두 chunk화 하고 chatgpt에게 물어볼 때 같이 정보를 넘긴다. 
