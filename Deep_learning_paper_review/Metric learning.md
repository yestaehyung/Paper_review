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
