나동빈 선생님의 강의를 듣고 논문을 분석하는 프로세스


기존 Seq2Seq 모델들의 한계점
- 단어를 입력으로 받을 때마다 hidden state를 갱신하는데, 이 hidden state는 소스 문장의 context vector이다.
- context vector v에 소스 문장의 정보를 압축한다. 
	- context vector는 고정 크기이기 때문에 bottleneck이 발생하여 성능하락의 원인이 된다.
- 디코더가 context vector를 매번 참고할 수 도 있다.
	- 그러나 여전히 소스문장을 하나의 벡터에 압축해야한다.
- 하나의 문맥 벡터가 소스 문장의 모든 정보를 가지고 있어야 하므로 성능이 저하된다.
- 그렇다면 **매번 소스 문장에서의 출력 전부**를 입력을 받으면 어떨까요?
	- 최신 GPU는 많은 메모리와 빠른 병렬 처리를 지원하기에 가능하다.

Seq2Seq with Attention
- Seq2Seq 모델에 attention 매커니즘을 사용
	- hidden state를 모두 저장한다. 
	- 디코더는 인코더의 모든 출력을 참고할 수 있다. 
	- context vector만 참고하는 것이 아닌 hidden state를 반영하고, 어떤 hidden state에 attention 해야하는지 학습한다.
- 디코더는 매번 인코더의 모든 출력 중에서 어떤 정보가 중요한지 계산한다. 
	- 가중합을 사용하여 계산한다. 
	- 각각의 단어 중에서 어떤 것을 가장 참고하면되는지 계산한다.(비율을 계산해서 hidden state에 곱을 한다.) 
	- E -> 모든 출력값 중에서 어떤 값과 가장 연관이 있는지 수치로 계산하는 것
	- W-> softmax에 넣어서 비율로 계산하는 것
- 이러한 attention 가중치를 사용해 각 출력이 어떤 입력 정보를 참고했는지 알 수 있다. (시각화도 가능하다.)

Transformer
- 2021 기준으로 현대의 자연어 처리 네트워크에서 핵심이 되는 논문이다.
- 트랜스포머는 RNN CNN을 전혀 활용을 하지 않는다. 
	- 대신 Positional Encoding을 사용한다.
- BERT와 같은 향상된 네트워크 에서도 채택
- 인코더와 디코더로 구성
	- Attention 과정을 여러 레이어에서 반복된다.

트랜스포머의 동작 원리: 입력 값 임베딩(Embedding)
- 트랜스포머 이전의 전통적인 임베딩은 아래와 같다.
	- ![200](https://i.imgur.com/ZsT4tIR.png)
	- 이 때 RNN을 사용하지 않으려면 위치 정보를 포함하고 있는 임베딩을 사용해야한다. 
		- 이를 위해서 트랜스포머에서는 Positional Encoding을 사용한다. -> 위치가 어디 있는지 알려줌  
		- 임베딩이 끝난뒤에는 attention을 진행한다. 
		- ![200](https://i.imgur.com/zKCjYxf.png)
		- encoder에서 진행하는 attention은 self-attention이라고 해서 각각의 단어가 서로에게 어떤 영향을 가지고 있는 것인지 학습하는 것이다. 어떤 단어가 연관성이 높은지?
		- 전반적인 입력 문장에 대한 문맥을 학습한다. 
	- 성능 향상을 위해 Residual Learning을 사용한다. 
		- 
![Uploading file...8arfr]()





