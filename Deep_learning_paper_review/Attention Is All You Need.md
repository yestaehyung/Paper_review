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
	- 디
