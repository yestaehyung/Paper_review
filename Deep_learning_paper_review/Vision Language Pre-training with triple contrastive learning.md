
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

TCL 은 CMA, IMC, 

