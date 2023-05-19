# Abstract

이전의 연구 접근은 간단한 image-text pair에만 집중하고, 다른 modal의 semantic connection을 무시했다.    
Knowledge base pretrain framework를 제안-Knowledge CLIP.    
CLIP에 semantic한 정보를 주입한 방법, 이러한 방법을 통해서 높은 퀄리티의 vision 과 language modal의 represnetaion을 align시킴    

# Introduction

VLP -> 각각의 모델을 each specific task에 훈련하는 것이 아닌 다양한 modal을 인식하고 포괄적인 task를 다루는 것을 목적으로 하고 multi-modal data에 대해서 representation을 학습하고, downstream task에 쉽게 접근할 수 있도록 함       

이전의 VLP들은 image에서 object를 detecting 하여 word token 과 align을 맞추고자 함, 그러나 이러한 방법은 추가적인 resource가 든다는 단점이 있음    

CLIP은 400 million의 image-text pair dataset으로 이미지를 학습함    
다양한 논문이 여기서 영감을 받아 시작함 -> including data modality[72], downstream tasks[57], training data efficiency[19, 44].   

현재 pre-training framework는 문제가 있다.
- pre-training에  사용되는 data pair가 단순하게 구성이 되어있다는 것이다. match or unmatched로만 그들의 관계를 표현하려 한다.
- 아래 그림과 같은 문제도 발생한다. imagenet zeroshot 문제인데, 두 scripts가 비슷하지만 다르다는 것이 있다. 
- 이러한 결과는 모델이 제한되고, VQA와 같은 task에서 좋지 못한 성능을 보여준다.

![](https://i.imgur.com/qRGa3tt.png)

이러한 semantic perceiving 에 관한 pre-train 모델의 한계를 다루기 위해, 저자들은 KG를 추가하였다.     
KG는 entities와 relation으로 구성된 large scale semantic network이다.    
data의 구조에 graph strucutre를 적용하는 것을 통해서, KG는 풍부한 정보를 줄수 있게된다.    


### 문제 해결 방안

To address the limitation of pre-trained models on semantic perceiving, we resort to the technique of knowledge graph, which has been widely studied in the field of natural language processing [7, 58]. Knowledge graph (KG) is a large-scale semantic network that comprises entities as nodes and semantic relations as edges. Through organizing data in a graph structure, knowledge graphs provide rich information on describing the relations between entities and enable a reasoning process through the whole graph. These advantages over regular-structured data are favorable on various tasks including question-answering [18, 70], relation prediction [29, 43] and knowledge reasoning [6, 59]. In recent years, knowledge graph has also been investigated in the field of computer vision, e.g., scene graph [65], and the integration of both language and image [2]. This bridges the gap between different modalities in the knowledge graph, which inspires us to explore a new knowledge-based pre-training framework, and inject semantic information into simple image-text pairs.    


이 논문에서 하려는 것 

In this paper, we propose a novel vision-language pre-training approach, dubbed Knowledge-CLIP, by constructing a knowledge augmented pre-training framework based on the widely used CLIP models. As illustrated in Fig. 2, we follow the structure of CLIP, and use two Transformer-based models as image and text encoders respectively. These two encoders take entities and relations in the knowledge graph as input and extract raw features for both entities and relations. Notably, entities can be in the form of image/text, while the relations are constantly described by language tokens. Then, a multi-modal Transformer encoder is adopted to fuse the entity features conditioned on their relations. In this way, the pre-trained model is pushed to concentrate on understanding semantic relations between visual and word concepts, thereby establishing strong semantic connections between vision and language modalities.


# CLIP

### clip의 문제점

CLIP은 두개의 분리된 이미지, 텍스트 인코더를 사용함. Image encoder는 ResNet 기반을 사용할 수도 있고, ViT 기반을 사용할수도 있음, BERT도 다양한 종류를 사용할 수 있음. ViT가 기본적으로 더 좋다고 밝혀짐, 이 논문에서는 transformer를 사용하는 모델만 고려가 된다. text input과 image input 모두 patch로 바뀌고 POS가 추가된다. 

이렇게 단순한 것의 문제는 아래와 같음
1. pre-training network가 data 구조의 단순한 것 때문에 입력의 sematic information을 잘 학습하지 못한다.
	1. 이렇게 되면 VQA, visual commonsense reasoning 과 같은 추론 능력을 필요로 하는 task에 대해서 성능이 안나온다
2. image와 text feature가 분리된 공간에 있어서, 모델이 다른 모달리티에서 상호작용을 어렵게 만든다.
3. 처음부터 모든 것을 pre-train하기에 시간 소요와 같은 너무 어려운 문제가 있다. 


# Knowledge Graph

일단 지식 정보를 Knowledge base로 바꾸고, 이를 다시 graph로 변경함

Knowledge base에서는 subject, object, relation으로 구성이 되어있다면,
Knowledge graph에서는 Node, Node, edge로 구성이 되어있음



# Knowledge-CLIP

위에서 이야기한 CLIP의 문제점을 바탕으로 KG를 바탕으로 하는 pre-train framework를 제안한다. 
1. we introduce knowledge graphs into the training dataset where the graph-structured data and semantic relations between concepts enable the model to extract semantic features and establish semantic connection across inputs
2. multi-modal encoder is added on top of the current image and text encoders to fuse the features from different modalities, and model the joint distribution between inputs
3. A continuous learning strategy based on the pre-trained model of CLIP is adopted which avoids the massive computation cost in the pre-training procedure, and enhance the generalization power of the model efficiently

## Data preparation

CLIP의 input과 달리 이 논문은 KG를 입력으로 받는다. head, tail, relation 이 트리플렛이 들어가게 되고    
여기서 학습에 사용한 데이터는 VisualSem, VisualGenome, ConceptNet 이 세가지가 된다. 

1. multi-modal knowledge graph
	1. Entities가 image, text를 모두 포함하게 된다. 
	2. 이것은 semantic connection을 vision과 language 사이에 만들어 준다. 
	3. 이렇게 되면 트리플렛은 (Img, Rel, Img), (Text, Rel, Img), (Text, Rel, Text) 이렇게 구성이 된다. 
		1. 풍부한 정보를 모달리티간에 교환을 할 수 있다.
2. scene graph
	1. Visual concept를 뽑는다. 예를 들어서 image에 장소와 연관된 미리 정의된 sematic relation 설명이 같이 있음
	2. 이렇게 될 경우 (Img, Rel, Img)의 트리플렛이 구성이 된다. 
	3. 두개의 엔티티가 같은 이미지의 다른 구역에서 나오게 된다묜, model은 더 fine-grained한 특징을 추출할 수 있다.
3. language-base knowledge graph
	1. (Text, Rel, Text)의 트리플렛으로 구성이 되어있다. word token끼리의 semantic한것을 align할 수 있다. 


## Model Architecture

encoder 지나고 나서, pooling이 있는데 효율 + local region에 대해 loss를 줄이기 위해 pooling을 제거함, 그런데 relation의 경우 한개 또는 두개의 token으로 구성이 되기 때문에, pooling을 제가히지는 않았다.

## Training Targets

Triplet-based loss



전반적으로 KG와 Graph loss에 대해 공부를 해야할 것 같음

![1000](https://i.imgur.com/eukmRCR.png)
