e-clip은 네이버 쇼핑의 멀티모달 사전학습 모델로 CIKM22 applied section에 accept 되었다고 한다. 

- 상품의 카테고리 분류
- 상품 속성 추출
- 상품 옵션 인식
- 동일 상품 매칭과 동일 상품 군집 자동화
- 성인 상품 등 부적절한 컨텐츠 제거
- 유사상품, 관심상품 추천

여러 task 를 해결하기 위해 model을 많이 사용하는데, 이 때마다 일일이 다른 모델을 개발하여 사용하기에는 어려운 문제가 있다.  
그래서 잘 pre-trained 된 model을 가지고 transfer learning 하여 여러 task 에 적용한다. 

네이버 쇼핑의 목표는 구매자가 원하는 상품/원하지 않는 상품을 빠르게 필터링 할 수 있는 기능을 만드는 것을 목표로 함.  
아래 그림은 네이버 쇼핑의 pull 구조도 임.

아래 빨간 색 부분을 간소화 하면 굉장히 효율적인 처리를 할 수 있음.  
굉장히 많은 unlabled data를 어떻게 활용하면 좋을지에 대한 탐구, self-supervised learning을 사용하자!  
CLIP 기반의 model을 개발함,  

![](https://i.imgur.com/LXsCvLW.png)

---

# Intro
## 배경
수백만명의 사용자가 사용하는 검색시스템에서 다양한 task를 지원하는 것은 사용자 경험을 향상시키는데 큰 도움을 함  
이럴 때 일반적으로는 여러 머신러닝 모델을 사용하여, 또는 단일 프레임워크를 사용하여 개발하였기 때문에 관리나 새로운 task에 대한 대처 같은 것들이 어려웠다.  

그런데 이제 CLIP이나 ALIGN과 같은 대규모 vision + text 모델의 VLP 방법론이 등장하면서 위에서 제기한 문제를 해결할수 있지 않을까라는 생각을 들게 하였다.  
여기서 말하는 두 모델의 장점은 아래와 같다
1. 다운 스트림 작업에서 높은 정확도를 보여준다. 경우에 따라서 fine-tuning 하지 않아도 높은 정확도를 보인다.
2. 이런 모델은 두개의 독립된 모델이 존재한다(image, text) 따라서 독립적으로 task에 활용할 수 있다는 것이 장점이다.
3. 레이블이 없는 데이터에서도 잘 작동한다. 

## 문제
이렇게 좋은 모델이 나왔는데, 이 것을 아직 전자 상거래에서 사용할 수 있을 만큼의 방법이 충분하게 논의되지 않았다.  
막상 전자 상거래에 적용을 하려고 해도 어려움이 많다.  
1. 데이터에 노이즈가 많다 -> 네이버 이커머스의 특징상, 수많은 사람들이 제품을 등록하고, 이에 따라 데이터 노이즈가 발생하게 된다. 또한 제품의 제목에 관련 없는 정보는 모델의 학습을 방해한다.
2. 중복, 유사 제품 -> 판매자가 동일한  상품을 여러번 등록하게 될 경우, 훈련 중에 이러한 상품을 모델이 다르게 학습하게 된다. 이는 contrastive loss 에 방해하게 된다.
3. Irregularity and Sparsity -> 전자 상거래의 제품 텍스트는 제품에 대한 요약된 세부 사항으로 구성되며 문법에 대한 구조가 부족하다?(제대로 된 설명이 부족한 상품이 많다.)
4. 제한된 컴퓨팅 자원 -> 이러한 모델은 많은 컴퓨팅 자원을 필요로 하기 때문에 이를 고려해야한다. 
5. Model convergence -> 대규모 배치를 가지는 경우 수렴 속도가 늦다. 

## 이 논문에서 하려고 하는 것
위에서 말한 문제를 해결하기 위해 e-CLIP을 제안한다. NAVER SHOPPING의 전반적인 구조에 대해 설명하고, 학습한  e-CLIP을 어떤 downstream task에 활용할 수 있을지 확인한다. 

## Contributions
- 산업에서 contrastive learning을 적용한 첫번째 연구이다. 
- 중복되는 제품에 상관 없이, 대규모 NAVER Shopping 데이터를 활용하여 학습할 수 있는 효과적인 학습 플랫폼인 e-CLIP을 제안한다.
- 전자상거래에 있어서 VLP를 하는데 문제를 발견하고, 해결하기 위한 접근을 제안한다.
- 다양한 실험을 통해서 제안한 프레임워크가 효과가 있다는 것을 보여준다.
- 산업 시나리오에 e-CLIP을 적용하고 긍정적인 피드백을 확인하였다.

# RW

## Deep learning in E-commerce
## Transfer Learning
## Multimodal Learning

# System Architecture


## Data preparation

1. 데이터 수집
	- 네이버 쇼핑에 올라오는 데이터를 사용
	- 네이버 쇼핑의 경우 상품을 업로드하는데 룰이 존재함
		- product title, price, brand name, set of images 를 함께 올려야함 
		- 팔수 있는 것인지, 매진되었는지
	- 제품은 classification을 통해 category를 할당받고 비슷한 상품이 있는지 DB에서 확인한다. 
2. 데이터 전처리
	- corrupted data, duplicate products, skewed data distributions 를 해결하기 위해 노력
	1. Invalid product
		- image text pair가 valid하게 구성하는 것은 매우 중요함. 그러나 데이터를 수집하는 과정에서 mismatched 한 데이터가 있을 수 밖에 없음, **No images, too small images, corrupted images**들을 rule-based 한 방법으로 제거함, invalid한 text도 product title의 token set을 비교하여 버림, 특수 문자를 공백으로 하고 나서, token이 2개 이하인 것은 버렸다
	1. Duplicate Products
		- 중복되는 product를 제거함, 일단 identical 한 title로 drop 하고, product image를 (5,5) 패치로 나누어서 각 패치의 평균 색상 값에서 한자리 숫자의 해시 키를 생성한다. 해시 값이 동일한 image를 제거한다. 모든 이미지에 대해서 ImageNet으로 훈련한 ResNet-34의 last layer를 추출해서 같은 경우 제거한다. 
	1. Inappropriate Products
		- 이상한 이미지(성인, 광고) 이런 것들을 버림

위와 같은 과정을 통해서 1B pair의 dataset을 330M pair로 줄이고 NAVER Shopping data로 부르기로 한다. 또한 더 짧은 학습과 baseline의 모델과 비교하기 위해 270M pair로 구성된 미니 데이터셋도 구축하였다.  

--- 
## Pre training Method: E-CLIP

![](https://i.imgur.com/GIkSQOw.png)

Pretrain을 할 때 Clip과 LiT에서 제안한 contrastive loss를 기반으로 진행하였다. 그러나 중복된 product와 메모리, 학습 속도를 고려해서 차이를 두었고 사전학습 한 모델은 downstream task에 활용하였다.  

- LiT -> zero-shot task를 할 때 image-encoder는 pretrain-model 가지고와서 freeze하고 text는 scratch 부터 학습하는 것이 좋다는 내용의 논문

e-clip 자체의 구조는 원본과 동일하지만, e-commerce의 특징상 중복되는 데이터가 있기 때문에 sampling 을 할 때 category 기반 방식을 사용함. 또한 computation 적인 것을 줄이기 위해 노력함  

-> 거대 데이터 + e-commerce에서 발생할 수 있는 contrastive loss의 문제점 + computational power들을 어느정도 해결해서 사용함 

### 3.3.1 Model architecture

- e-CLIP의 구조는 원본 CLIP과 동일하게 dual encoder 구조를 따른다.  
- CNN이 많은 vision task 에 활용되지만, computational effciency를 고려해서 ViT-B/32 를 image encoder로 사용하였다. (CNN보다 ViT가 더 짧은 GPU load와 훈련 시간을 가지고 있음)
- Data의 irregularity and sparsity를 고려해서 BERT를 text encoder로 사용하였다. 
	- Multiple language가 가능하다고 설명을 하였기는 함
- ALIGN, CLIP 에서 CLS 토큰을 representation으로 사용했던 것 또는 BASIC 에서 사용하였던 representation의 평균을 사용하는 것 보다 **e-CLIP의 last layer에서 representation의 평균을 계산함**

### 3.3.2 Training objective 

- InfoNCE loss는 유사한 pair가 cosine sim이 높도록, 유사하지 않은게 cosine sim이 낮도록 학습하는 loss임
- **그러나 네이버 쇼핑 데이터셋은 중복되는 데이터기 많기 때문에, 같은 상품끼리 negative pair를 형성해서 학습이 잘 안이루어 질 수도 있다!** -> 우리도 동일함,
- 위의 상황을 다루기 위해 catalog-based soft labeling 으로 InfoNCE loss를 수정하였다. 
- 네이버 쇼핑 데이터에서는 i 번째와 j번째의 데이터가 겹칠 수 있다. 그러나 clip의 특성상 i - i 번째 pair가 positive pair(1)로 계산이 된다. 그러나 만약 데이터가 겹치게 되면 j 번째 데이터가 negative로 규정을 해버리게 된다. 그래서 이것을 보완하기 위해 카탈로그를 사용하였다. 