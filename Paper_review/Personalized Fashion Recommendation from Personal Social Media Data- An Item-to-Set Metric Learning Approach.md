# Intro
SNS의 발달으로 사람들이 방문한 곳, 먹은 것 outfit 같은 것들을 올린다. 그리고 Fashion이 주가되는 online communities 가 있다. 

Lookbook.nu -> 자신들의 패션 선호를 보여주면서 다양한 스타일을 올리는 곳
##  본 논문에서 하려는 것
소셜 미디어 유저의 활동을 기반으로 fashion outfit을 추천하는 개인화된 패션 추천의 문제점을 파악한다. 
SNS 데이터의 문제점은 단지 셀카에 지나지 않는 다는 것에 있다. 그래서 우리가 일반적으로 알고 있는 패션 데이터셋과는 다른 면이 있다. 

이러한 다른 면 때문에 현재 나와 있는 SOTA 모델은 본 논문의 task를 해결하기 힘들다. 왜? labeling 이 되어 있지 않기 때문에
selfe post 들의 fine-grained supervision 없이 본 논문에서는 개인화된 패션 추천에  self-supervised 접근을 사용한다. 

사용자의 selfie post를 자신의 패션 취향을 드러내는 set으로 다룬다. 
추천하는 아이템을 items라고 한다.

그래서 item-to-set metric을 사용하여 set과 item 간의 개인화된 유사도를 측정한다. set과 user의 Item간의 거리는 가깝게, set과 다른 유저들의 item간은 멀게 학습하게 된다. 

## Metric learning


# Related works
## Fashion Annotation
- 패션 요소를 태깅하여 자동 패션 분석을 용이하게 하게 위해 수행하는 task
- parsing, recognition, attributes annotation, landmark detction이 있다.
	- parsing
		- pixel level에서 garment items를 예측
		- semantic segmentation을 활용
	- Attribute annotation
		- clothing image에서 fashion attribute 태깅하기
## Fashion Retrieval
- 사람 이미지 쿼리에서 비슷한 옷을 찾는 task
- 가장 흔한 접근은 attributes를 fashion representation 학습에 활용하는 것이다.
## Fashion composition
- 입은 item들이 compatible한지, visual 적으로 fashion item들 끼리 완벽한지
## Fashion Recomendation
- 개인화된 패션 추천이 중요하다. 

# Data Construction

Lookbook.nu라는 outfit과 selfie를 올리는 fashion focused website에서 sns 데이터를 수집

2,293 명의 user를 선정, 각 유저당 100개의 최근 게시물(사진, 타이틀, 해시태그)를 수집
각 유저들은 7,000명의 팔로워 이하로만 수집 -> 광고가 있을 수도 있기 때문에

## Data Overview


![](https://i.imgur.com/G5tsdi6.png)

해시태그의 경우 styles of outfits(street, blogger, summer) 내용 담고 있었고
제목의 경우 조금 더 특징적이고 자세한 설명을 담고 있었다. 

![](https://i.imgur.com/rGcamEX.png)

## Data Preprocessing
- Image data preprocessing
	- raw 한 selfi image는 여러 개의 종속된? 사진을 포함하고 있어서 Yolov3를 사용하여 사람들을 crop하고 가장 점수가 높은 사람을 선택하였다.
	- Grayscale image는 제외하였는데, outfit style에 색상이 많은 영향을 주기 때문이다.
- Word data preprocessing
	- Title과 hashtag 의 경우 Wikipedia로 pretrained 한 GloVe text embedding을 사용하여 feature를 추출하였다.
	- hashtag의 경우 Viterbi algorithm을 적용하여 word segment하였다.
		- 각각의 단어를 embdding 하였다.
- 각각의 feature가 추출되면 단순히 concat 했다. 

# Method
1. Multi - modality feature extraction
2. Multi - interest awareness 
3. User uniqueness

위 3가지를 반영할 수 있는 방법을 사용하였다. 

## Fashion Item Embedding Module

muti-modal한 user activities는 personal preferences를 보여준다.
Fashion information을 뽑기 위해서 fashion item embedding module을 사용하였다.

![](https://i.imgur.com/fab02Kp.png)

위 그림은 image-hashtag-title triplets에서 fashion 정보를 뽑아내는 방법이다. 
x = (x<sup>(im)</sup>, x<sup>(h)</sup>, x<sup>(t)</sup>) -> 이런 형식의 triplets

1. Image Feature Extraction
	- Image inputs -> x<sub>im</sub> 은 outfit combination과 선호하는 appearene를 보여줌 
	- [body parsing model](https://arxiv.org/pdf/1804.01984.pdf)을 사용하여 11개의 garment regions를 뽑아냄 
		- 사용하는 regions는 dress, coat, pant, skirt룰 사용
		- 사용하지 않은 것은 face, hair, background, socks sunglasses 등
	- [pre-trained image recognition model](https://arxiv.org/pdf/1409.1556.pdf) 사용 (VGG-19)하여 visual information을 각 garment region에 대해 추출
	- VGG 모델의 conv1, conv2의 결과를 계산, 각 garment region으로 평균을 낸다. 
	- 모든 garment regions의 feature을 concate함
	- 결과적으로 2112 차원의 특징 vector 를 얻게되었다.
1. Hashtag Feature Extraction
	- x<sup>(h)</sup> = {1<sup>(h)</sup>, ... , m<sup>(h)</sup>}의 word embedding으로 구성되어 있다. 
	- 만약 hashtag가 없는 경우 zero vector가 사용된다.
	- 다른 단어가 같은 fashion style을 나타낼 수도 있음 
		- e.g., corset, leatherjacket, black 이라는 단어는 모두 goth style을 나타냄
	- 위와 같은 이유 때문에 MLP를 구현하여 일반 word embedding에서 fashion-related embedding으로 변환하였다.
	- 이미지처럼 고정된 길이의 feature을 뽑기 위해서 attentive averaging operation을 사용
		- hashtag의 embedding feature의 길이가 매우 다양하기 때문!
		- ![](https://i.imgur.com/H0kL19b.png)
		- <sup>(h)</sup>는 hashtag feature로 사용됨
1. Title Feature Extraction
	- x<sup>(t)</sup> = {1<sup>(t)</sup>, ... , m<sup>(t)</sup>}의 word embedding 으로 구성
	- hashtag과 같은 방법을 사용하여 <sup>(t)</sup>를 feature로 사용 
3. Cross-modality Gated Fusion
	- featre의 quality를 높이기 위해 fusion을 사용하였다. 
	- title과 hashtag이 image와의 차이점은 덜 noisy하고 semntic info를 보완할 수 있다는 것이다. 
	- 그래서 일단 title과 hashtag를 아래와 같이 cross-gating한다.
		- ![](https://i.imgur.com/h4VUfsM.png)
		- ![|100](https://i.imgur.com/yKXofzO.png)
		- 위 그림을 보고 이해하면 될 것 같다. 
		- 만약 비슷한 패션의 경우 crossed-filtered feature는 low-level image feature를 걸러내는데 사용할 수 있다
		- image의 경우 아래와 같다.
			- ![|200](https://i.imgur.com/OfrUwuj.png)
		- 마지막으로 2-layer MLP가 모든 feature을 concat한다. 
## Item-to-set Metric  Learning 

사용자의 selfie posts -> S = {<sub>1</sub>, ... , <sub>k</sub>} 에서 similar 측정

1. Item-to-set Similarity Metric
	- Metric learning 은 two item간의 similarity를 학습하기 위한 것이다. 
	- 이전 metric learning의 접근은 two item i와 j의 feature points *i*, *j* 간의 point-wise distance *d(i, j)* 를 사용하여 두 아이템간의 유사도를 측정함
		- *d(i, j)* 는 *l*<sub>2</sub>  거리를 사용하여 계산
	- Item-to-set metric은 초개인화 추천을 위해 개인의 selfie에서 얼마나 비슷한 outfit 후보를 찾아서 계산하는 것이다.
	- 본 논문에서는 두개의 item-to-set metric의 약점에 대해 설명한 후 어떻게 사용하였는지 설명한다.
		- averaged item-to-set distance
			- Set에 있는 모든 item들과 item *f* 간의 거리 평균을 계산하는 방법
			- ![|200](https://i.imgur.com/EKLqdJ0.png)
			- 저자들이 주목하는 것은 아이템간 거리 평균 = 아이템의 feature 평균 후 거리 계산
				- 이 때 가정은 거리 계산 알고리즘이  *l*<sub>2</sub>  거리 라는 것 
				- 다른 few-shot learning 에서도 아이템 feature 간 평균 해서 거리 구한 적이 있다.
		- nearest-neighbor item-to-set distance
			- Set에 있는 모든 아이템과 query  아이템 *f* 의 가장 짧은 거리 고려 
			- ![|200](https://i.imgur.com/jr7fgYB.png)
			- ![|200](https://i.imgur.com/DiOzOE0.png)
		- 이 두개의 거리 측정 방법 모두 drawback 이 있다. 
			- average distance -> S 가 여러개의 패션 스타일을 포함하고 있을 때 similartiy 계산을 하기 힘들다
			- nearest-neighbor -> 여러개의 패션 스타일에 더 적용하기 쉽지만, minimum 계산은 outliers와 noise에 취약하다. + 학습 동안 가장 가까운 item에만 feature를 업데이트 한다.
		- 본 논문에서는 generalized item-to-set distance을 사용
		- set S 와 query *f* 가 있을 때 *w*<sub>i</sub> (importance weight)를 각 set의 item <sub>i</sub> 에 할당 
			- feature averaging과 distance computation 전에 할당
			- importance weight 은 importance estimator ![|100](https://i.imgur.com/MoMGeQK.png) 를 계산하는 데 사용된다. 
		- Item-to-Set distance는 아래와 같음
			- ![|200](https://i.imgur.com/kyXJs2k.png)
			- 다중 분류에 사용되는 sigmoid
		- ![|100](https://i.imgur.com/MoMGeQK.png) 는 constant value 거나 ![|100](https://i.imgur.com/X9fZFVY.png) 이다. 
1. Importance Estimation
2. User-specific Metric Space






