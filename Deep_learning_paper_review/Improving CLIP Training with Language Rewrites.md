
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

-> 지금 여기서 확인해야하는것, dataset에서 몇개를 뽑아서 chatgpt에 넣었는지??      
# llama 공부

https://github.com/facebookresearch/llama

우리가 어떻게 활용할 수 있을지...?       


WSDM에서 사용하는 데이터랑 우리가 사용하는 데이터가 유사하다는 것을 확인해야한다. 
이쪽 도메인에서 많이 쓰이는 모델(성능비교) 다 가지고 온다, 

결국에 비교 데이터셋이 짧은 데이터셋인데, llama를 써서 aug된걸 넣게 되면, 원래 짧은 텍스트를 잘 예측하게 되야하는데 이게 잘 될지 의문이 있다.      

효과성을 보이는데 있어서 어떤 데이터를 택할 것인가가 중요하다.        

사람의 knowledge에서 온 attribute를 잘 이야기해야할 것 같다.    
무조건 벤치마크 하면 좋을 것 같다       
 