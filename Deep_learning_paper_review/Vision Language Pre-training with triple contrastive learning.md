
MI: mutual information
CMA: Cross modal alignment
TCL: triple contrastive learning
VLP: vision language pre-training 
VQA: vision question answering 
IMC: intra modal contrastive
LMI: local mutual information maximization

Self supervision은 vision and language representation learning 에서 중요한 topic임.
전통적인 접근은 라벨링 되지 않은 엄청난 양의 데이터로 pretrain 하고, task 에 맞게 fine tuning 하는 것이다.
Vision에서는 using exemplars predicting the relative position between two random patches or via solving jigsaw 와 같은게 있고, Language는 MLM(mask language modeling이 있다)

VLP framework(massive image-text pair)
	Uniter:  Universal image-text representation learning.
	Large-scale adversarial training for vision-and-language representation learning
	Unimo: Towards unified-modal understanding and generation via cross-modal contrastive learning.
	Oscar: Object-semantics aligned pre-training for vision-language tasks.
	이러한 논문은 vision과 languagefeature을 concat하기 위한 encoder를 적용하는 것이 key.

InfoNCE loss?
	---

TCL 은 CMA, IMC, LMI의 세 contrastive module을 사용한다. 
Specifically, 
	i) CMA pulls the embeddings of matched image-text pairs together while pushing those of non-matched pairs apart by maximizing global MI between matched image and text; 
	ii) complementary to CMA, IMC maximizes agreement between differently augmented views of the same data example through maximizing their global MI; 
	iii) LMI encourages high MI between the global representation and every local region (e.g., image patches and text tokens) of the input, which is designed to remedy the side-effects that are introduced by the global MI maximization.

### VLP
	CLIP -> 어떤 text가 어떤 image와 일치하는지 예측
	ALIGN -> CLIP에서 추가적으로 noisy한 데이터를 활용(10개의 image-text pair)
	그러나 CLIP과 ALIGN은 vision-based downstream task에 맞게 디자인 되어있다. 
	VQA와 같은 vision+language task를 위해서 OSCAR, UNIMO, VILLA, UNITER는 faster r-cnn과 같은 object detection 모델을 먼저 사용해서 vision feature를 잡고, multi-layer transformer 를 적용해서 vision feature과 text feature를 concat한다.
	



## 유튜브 논문 정리 된 것 메모
### Intro
	pretrain -> fine-tune 하는 방식이 인기이다.
	사람들이 든 생각은 멀티모달로 활용하면 어떨까???
	Fusion encoder -> OSCAR, UNITER -> 이미지 임베딩하고 텍스트 임베딩이 다른 곳에 임베딩 된다.
	Albef -> maximize global MI, 이것도 문제가 있다. 
	- only co-occuring features are captured
	- fails to consider lacalized and strucstal information
	TCL ->triple contrastive loss 
### RW
	CLIP, ALIGN -> vision task 만 맞다
	OSCAR는 faster r-cnn을 사용한다.
	ViLT?(확인해 보아야하는 논문)
	ALBEF 가 이전에 있는 것들을 합친 느낌?
	- ITC를 적용, MOCO에서 영감을 받아서 negative pair를 생성, momentum??
	- 모멘텀을 사용하는 이유 -> positive pair 가 진짜 맞나? 네거티브라고 할 수 있나? 
	- MI?? -> 

