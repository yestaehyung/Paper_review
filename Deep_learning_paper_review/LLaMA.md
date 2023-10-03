# NLP
- Language Model
	- 나열된 단어들의 조합에 확률을 부여하는 모델
- Natural Language Understanding
- Natural Language Generation

Downstream task -> 모델의 성능 지표를 확인할 수 있음
- Natural Language Inference
	- 두 문장이 어떤 관계에 있는지 판별하기 (함의, 모순, 중립)
- Reading Comprehension
	- 지문에서 필요한 정보를 찾는 문제
- Common sense
	- 일반 상식으로 유추할 수 있는 내용을 묻는 문제
- Sentiment Analysis
	- 텍스트의 어조가 긍정적인지 부정적인지를 판별하는 문제
- Machine Translation
	- 번역 문제
- Summarization
	- 주어진 텍스트 요약하기

## Seq2Seq

순차적인 데이터를 입력받아 순차적인 데이터를 출력하는 모델 (여기서는 순차적인 자연어 토큰)    

![400](https://i.imgur.com/GROSXDn.png)

- encoder: 입력 시퀀스의 문맥을 반영해 context vector를 생성
- decoder: context vector를 seed로 사용하여 순차적으로 출력을 생성

![400](https://i.imgur.com/C1C7J70.png)

두 개의 순환신경망 구조로 이루어진 모델    
- encoder: LSTM 모델 
	- context vector: encoder LSTM의 마지막 time step에서의 hidden state
- decoder: LSTM 모델
	- context vector: 0번째 hidden state로 간주하여, 첫번째 decode LSTM의 입력이 됨 
- ![400](https://i.imgur.com/8OcMdhi.png)

Seq2Seq 모델의 단점, 문장에는 더 중요하고 덜 중요한 단어가 있는데 입력이 길어지게 되면 앞 부분의 정보가 희석이 된다는 문제가 있다.     
어떤 단어가 중요한지 파악하는 것이 중요하다    

Bahdanau attention을 추가하여 문제를 완화할 수 있음     
디코더에 문맥 벡터를 추가한다.  (어떤 벡터를 중요하게 봐야하는지 학습할 수 있다.)
![400](https://i.imgur.com/Rk5ADPi.png)

![](https://i.imgur.com/Gilqk2r.png)
