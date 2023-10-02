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
