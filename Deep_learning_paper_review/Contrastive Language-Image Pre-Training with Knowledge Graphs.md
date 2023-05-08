# Abstract

이전의 연구 접근은 간단한 image-text pair에만 집중하고, 다른 modal의 semantic connection을 무시했다.    
Knowledge base pretrain framework를 제안-Knowledge CLIP.    
CLIP에 semantic한 정보를 주입한 방법, 이러한 방법을 통해서 높은 퀄리티의 vision 과 language modal의 represnetaion을 align시킴    

# Introduction

VLP -> multi-modal data에 대해서 representation을 학습하고, downstream task에 쉽게 접근할 수 있도록 함    
이전의 VLP들은 image에서 object를 detecting 하여 word token 과 align을 맞추고자 함, 그러나 이러한 방법은 추가적인 resource가 든다는 단점이 있음    

CLIP은 400 million의 image-text pair dataset으로 이미지를 학습함    
다양한 논문이 여기서 영감을 받아 시작함 -> including data modality[72], downstream tasks[57], training data efficiency[19, 44].   


### 문제 상황

Specifically, the data pairs for pre-training are organized in the simplest manner, where only the descriptions of matched and unmatched are used to represent the relation between a given image and text pair. This usually leads to a degenerated scenario, where the model tends to rely on the co-occurrence of inputs instead of their semantic meanings.     

### 문제 해결 방안

To address the limitation of pre-trained models on semantic perceiving, we resort to the technique of knowledge graph, which has been widely studied in the field of natural language processing [7, 58]. Knowledge graph (KG) is a large-scale semantic network that comprises entities as nodes and semantic relations as edges. Through organizing data in a graph structure, knowledge graphs provide rich information on describing the relations between entities and enable a reasoning process through the whole graph. These advantages over regular-structured data are favorable on various tasks including question-answering [18, 70], relation prediction [29, 43] and knowledge reasoning [6, 59]. In recent years, knowledge graph has also been investigated in the field of computer vision, e.g., scene graph [65], and the integration of both language and image [2]. This bridges the gap between different modalities in the knowledge graph, which inspires us to explore a new knowledge-based pre-training framework, and inject semantic information into simple image-text pairs.    


이 논문에서 하려는 것 

In this paper, we propose a novel vision-language pre-training approach, dubbed Knowledge-CLIP, by constructing a knowledge augmented pre-training framework based on the widely used CLIP models. As illustrated in Fig. 2, we follow the structure of CLIP, and use two Transformer-based models as image and text encoders respectively. These two encoders take entities and relations in the knowledge graph as input and extract raw features for both entities and relations. Notably, entities can be in the form of image/text, while the relations are constantly described by language tokens. Then, a multi-modal Transformer encoder is adopted to fuse the entity features conditioned on their relations. In this way, the pre-trained model is pushed to concentrate on understanding semantic relations between visual and word concepts, thereby establishing strong semantic connections between vision and language modalities.


# CLIP

### clip의 문제점

This simple training framework actually brings several concerns that need to be addressed. First, the pre-training framework fails to model the semantic information of inputs due to the simplicity of the data structure. This results in inferior performances on tasks that require reasoning ability, e.g., visual question answering and visual commonsense reasoning. Second, the image and text features reside in separate spaces, which makes it difficult to model the interactions between different modalities. Third, the massive time and resource consumption in the training procedure set restrictions on performing a full pre-training schedule from scratch.

# Knowledge-CLIP

## Data preparation

## Model Architecture



전반적으로 KG와 Graph loss에 대해 공부를 해야할 것 같음