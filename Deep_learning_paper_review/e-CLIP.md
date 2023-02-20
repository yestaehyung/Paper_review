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
