
CVPR'23

Abstract
CLIP이 좋은 모델인데, data augmentation 측면에서 image만 augmenation을 진행함,     
이렇게 되면 text 측면에서 한 이미지에 대해 다양한 것이 입력이 되지 않는 것을 제한함?? -> 어떤 의미    

이논문은 language rewrites를 해서 CLIP의 성능향상을 하는 LaCLIP을 제안함    

Github이 있음    


Intro


CLIP을 학습할 때 text는 아무런 augmentation하지 않고 변하지 않는다는 것에 초점을 두고 있음 이렇게 비대칭되게 되면 같은 text인데 augmentation이 다르게된 image를 만나고 이건 아래의 두가지 문제를 발생시킴    

1) Firstly, the image encoders receive limited supervision from the language side since the same image is consistently paired with the same words. Consequently, the language aspect provides less guidance to the image encoders. 
2) Secondly, the text encoders repeatedly encounter the exact same texts in each epoch, which increases the risk of text overfitting and significantly impacts zero-shot transferability.

그리고 text augmentation의 하는 방법도 부족하다.        
- replacement
- masking
이 두방법 모두 image에 비해서 text를 풍부하게 만들어 줄 수는 없는 방법이다.    

GhatGPT로 text를 몇개 생성해서 llama에 학습하는 방식으로 text를 다시 생성하였다.    
이렇게 한 이유는 데이터가 정말 많은데 가격 측면에서 문제가 있기 때문이다, 우리도 이렇게 할 수 있을 것 같다...    


# llama 공부

https://github.com/facebookresearch/llama




