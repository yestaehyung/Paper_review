## Metric 
= Distance (거리)는 함수 이다.
D(x,y) = 0 <-> x = y
D(x, y) = D(y,x)
D(x,y) <= D(x, z) + D(z, y)

위의 조건을 만족한다. 

유클리디안 거리, P차 노름거리, 내적 거리, 코사인 거리, 마할라노비스 거리가 있다.

Metric space는?  
두 개체 사이의 거리가 정의된 공간  
= 유사한 개체는 가까이 유사하지 않은 개체는 멀리 위치하게 한다. 

거리와 기계학습 알고리즘 간에는 밀접한 관계가 있다.  
EX) k-means, K-NN  

Deep metric learning 이라는 것은 거리 공간을 학습하는 것이다.  

Softmax classifier 로 학습된 feature 는 한계가 있다.  
EX) face recognition -> Deep metric learning 이 우수한 성능을 보이는 computer vision 분야  
이미지 -> DNN -> embedding vector -> 확률값(softmax 취함) -> cross entropy 함수로 업데이트  
이렇게 softmax로 구분을 하게 되면, separable features 만 학습이 된다.  
그러나 정확한 학습을 위해서 Discriminative features를 학습할 필요가 있다.  
inter-class variation 은 크게 intra는 낮게 학습하는 방향  

Deep metric learning 의 loss 함수 종류  
1. Contrastive loss
1. Triplet loss
2. Center loss
3. Additive angular margin loss  

### Contrastive loss

- 가장 간단하며 직관적인 손실함수
- 두 개의 데이터가 유사하다면 거리가 작아지도록 두개의 데이터가 유사하지 않은 데이터라면 거리가 멀어지도록 손실함수가 고안됨
- 두 개의 이미지가 같은 weight를 공유하고 있는 DNN 에 들어가서 특징 추출을 하고, 같은 특징이라면 1로 아니면 0으로 레이블링 되어있다. 
- 같은 레이블의 거리는 줄어들게, 유사하지 않은 데이터의 경우 늘리는 방향으로 loss function이 구성되어 있다.
- **내 연구에서 어떻게 이것을 활용할 수 있을지?**
	- 같은 브랜드는 유사한 특징이 있기 때문에, 브랜드를 구별한다?
	- 같은 스타일이 조금 더 괜찮을 것 같기는 하다. 특징이 더 뚜렷할 것 같다. 
	- 스타일이 정의 되어있는 벤치마크 데이터셋을 구축할 필요가 있다.

### Triplet loss

- 가장 유명하고 널리 활용되는 손실 함수
- 세개의 데이터를 사용하여, positive pair 보다 negative pair의 거리가 더 멀어지도록 손실함수가 고안됨
- anchor 에서 margin 만큼 negative를 멀게 할 수 있다.

지금과 같은 방식은 label이 필요한 경우에 대한 것들이다(labeling 된 class 기준, 유사하냐 안하냐)  
그런데 같은 이미지에서 augment해서 유사한지 아닌지로 판단 기준을 세우게 되면 self-supervised learning 에 활용할 수 있다. 

# Contrastive learning

self-supervised learning -> Input data 자제에서 쉽게 얻을 수 있는 정보를 사용해서 좋은 representation을 학습

1. Instance Discrimination
	1. 레이블 정보 없이 이미지끼리 학습-공유하는 representation이 있을 것이다. 
	2. ![](https://i.imgur.com/nZiW88R.png)
---

## MoCo
- Memory bank 의 단점
	- 관측치 전체에 대한 embedding 정보를 계속 저장하고 있어야한다. - 메모리 이슈
	- 랜덤 샘플링을 통해 negative example을 구성 - 데이터 샘플별로 학습에 기여하는 정도가 다르다
- Memory Queue 를 사용
	- First In First Out, 모든 샘플이 동등하게 학습에 활용이 된다.
- Momentum Encoding
	- 과거 모델 weight들이 가중 평균으로 업데이트
	- 과거의 나 자신들이 'teacher'가 되는 mean teacher 방식과 동일(semi-supervised model)
	- **ALBEF 에서도 사용되는데, 내가 다시 확인해볼 필요가 있다.**
## SimCLR
- Queue도 사용하지 않고 batch size를 늘려서 negative 생성을 batch 안에서 해결해 보자
- 이미지에 대해서 2번의 data augmentation을 적용
- 그러나 4096의 batch size는 엄청난 연산이 필요하게 된다.
- 다양한 data augmentation 기법을 활용한다. 
- 더 좋은 feeture를 활용하기 위해 embedding layer를 깊게 쌓는다. 
## MoCo2
- SimCLR 에서 사용했던 방법론들은 MoCo에 적용한 것 
- 더 좋은 성능을 보인다.

## Define Example Nicely
- 어떻게 하면 좋은 positive를 얻을 수 있을 까? Negative는 어떻게 더 잘 뽑을 수 있을까?
- Prototype to Support Positive 
## Sample Hard Negatives
- Anchor 와 가까이 있는 hard negatives를 선택해야한다
- 관측치별로 주변 density를 측정하여 샘플링에 반영



