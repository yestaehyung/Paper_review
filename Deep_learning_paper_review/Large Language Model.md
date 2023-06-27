# llama 공부

https://github.com/facebookresearch/llama

우리가 어떻게 활용할 수 있을지...?       

상품 제목에서 바로 chatgpt를 쓰기에는 error가 들어가게 된다.         
어떻게 정확한 정보를 기반으로 상세 설명을 생성할 수 있을지?       
Human factor를 어떻게 넣을 수 있을지??         
패션 이미지를 대표하는 category attribute가 무엇일지..???????       
설명이 있는 데이터셋에서 뭔가 이끌어낼수 있을지...??????     

최신 기술 follow up이 필요함,,,,,,      fine-tuning을 어떻게 할 수 있을지...?????          
In-context learning은 어떻게 할 수 있을지??????           -> 이걸 전문가가 생성한다..????     
추천 시스템에 llm을 어떻게 활용할 수 있을지...?????????            

일단 면적을 사용해야한다. 면적이 가장 넒은 것이 여기의 대표 아이템이라고 할 수 있을 것 같다.    
그런데 생각이 나는건, 추천에 대한 설명을 생성해야하는데 지금까지 논의한건 아이템에 대한 설명을 생성하려고 하는 것 같다는 생각이 든다.    

Image feature 추천
- LLama-adapter v2 multimodal를 사용해서 추천 결과를 설명한다.
Attribute feature 추천
- attribute 결과를 사용해서 추천을 한다. 

**양자화 (Quantization)**
- 부동소수점으로 표현되는 파라미터들을 특정 비트 수로 줄이는 방법

상업적으로 사용가능한 것
- https://well-chauffeur-a16.notion.site/LLM-d23b30bc16c34c03b55185dcda442eae

LangChain
- 용량이 큰 문서를 쪼개는 역할을 한다. 
- Fashion 정보가 담겨있는 책을 LangChain으로 모두 chunk화 하고 chatgpt에게 물어볼 때 같이 정보를 넘긴다. 

평가방법 확인하기!      

성능 기준표
- https://tatsu-lab.github.io/alpaca_eval/

AutoGPT
- https://github.com/Significant-Gravitas/Auto-
- https://www.youtube.com/watch?v=CHzNNxZOIYI&t=15s
- 경쟁사 분석 시킬 수 있을 듯


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



WSDM에서 사용하는 데이터랑 우리가 사용하는 데이터가 유사하다는 것을 확인해야한다. 
이쪽 도메인에서 많이 쓰이는 모델(성능비교) 다 가지고 온다, 

결국에 비교 데이터셋이 짧은 데이터셋인데, llama를 써서 aug된걸 넣게 되면, 원래 짧은 텍스트를 잘 예측하게 되야하는데 이게 잘 될지 의문이 있다.      

효과성을 보이는데 있어서 어떤 데이터를 택할 것인가가 중요하다.        

사람의 knowledge에서 온 attribute를 잘 이야기해야할 것 같다.    
무조건 벤치마크 하면 좋을 것 같다       

