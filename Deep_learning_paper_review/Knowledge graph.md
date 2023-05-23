
https://www.youtube.com/watch?v=_THQzPiLvyI&t=474s


![](https://i.imgur.com/Uvk5Oxd.png)

## Steve Jobs and Steve Wozniak co-founded in Apple in 1977

### Named Entity Recognition

- ![](https://i.imgur.com/7TLC9Li.png)

### Relation Extraction

- Entitiy 사이의 관계를 추출한다. 
- <Steve Jobs, Apple> as founder
- <Steve Wozniak, Apple> as founder

위에서 얻은 정보로 알 수 있는 것

- (Head, relation, Tail)
- (Steve Jobs, is-founder-of, Apple)
- (Steve Wozniak, is-founder-of, Apple)
- 
![pNgqFL1.png](https://i.imgur.com/pNgqFL1.png)

Named Entitiy Recognition(NER)
- NE: Entitiy가 될 수 있는 고유명사 등의 것으로 목적에 따라 정의
- 적용 및 평가: NER tagging
	- BIESO: begin, inside, end, singletone, outside 
	- precision, recall f1-score를 통해서 token 단위의 tagging 성능평가 수행
- Traditional Approaches
	- Rule-based: 특정한 domain 혹은 한정적인 data 내에서 특정한 패턴을 규칙을 tagging
	- Unsupervised Learning Approaches: contextual similarity를 활용한 clustering 기반의 tagging
	- Feature-based Supervised Learning: multi-class classification, sequence lableing task
- Deep learning Approaches

Relation Extracktion
- 구조화 되지 않은 일반적인 text로부터 Entity Pair 사이의 Relation을 찾아내는 task
- Relation types: Dataset마다 조금씩 다른 형태를 가짐
- 이전에는 NER과 구분되어 순차적인 별개의 task로 활용하는 경우가 많았으나, 최근에는 NER과 RE가 한번에 동작하는 경우가 많다. 


# KG-x

NER을 어떻게 수행하는지?

Khan 에서 어떻게 했을까?

1. data 수집
2. entitiy, relation extraction
3. Data cleaning

219,915 post 276,156 post를 커뮤니티에서 수집 총 496,071개

18개의 political-related entities, Sota NER 방식을 사용하였다. -> fashion sota가 있나...?

