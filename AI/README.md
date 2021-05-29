# AI/ML
UCI에서의 AI 수업(CS171 & CS178)의 PPT와 구글링을 결과를 참고하여 작성했습니다.
</br><br>
## 목차
[용어 설명](#용어-설명)<br>
[Overfitting](#Overfitting)<br>
[Naive Bayes Classifiers](#Naive-Bayes-Classifiers)<br>
[Regression](#Regression)<br>
[Classification](#Classification)<br>
[Neural Network](#Neural-Network)<br>
[Reinforcement Learning](#Reinforcement-Learning)<br>
</br><br>

## 용어 설명
* **Machine Learning**: 인공 지능의 한 분야로, 컴퓨터가 학습할 수 있고 알고리즘과 기술을 개발하는 분야
* **Data Mining**: 대규모의 데이터에서 체계적이고 자동적으로 데이터를 분석하고 필요한 데이터를 추출하는 과정
* **Supervised Learning**: 정답이 있는 데이터를 제공하여 모델을 학습시키는 방법으로 classificaition과  regression이 대표적인 방법
* **Unsupervised Learning**: 정답이 없는 데이터를 제공하여 발견되지 않은 정보나 패턴을 발견하여 모델을 학습시키는 방법 (mostly used for unlabled data)
* **Reinforcement Learning**: 환경 속에서 보상이 주어지며 보상을 획득하는 모델 학습법
* **선형 회귀(Linear Regression)**: Supervised learning의 일종으로 종속 변수 y와 한 개 이상의 독립 변수 x와의 선형 관계를 모델링 하는 것 (e.g. 공부 시간이 늘어날 수록 시험 성적이 높아짐)
* **Classification**: Supervised learning의 일종으로 기존 데이터의 category에 따라 새로운 데이터의 type을 판별하는 것 (e.g. 스팸 처리)
</br><br>

## Overfitting
머신러닝에서 학습은 가장 중요한 역할을 한다. 학습이 어떻게 되느냐에 따라 결과가 달라지기 때문이다.

**Overfitting**은 학습이 과하게 많이 될 경우에 일어날 수 있는 문제를 다룬다. 과하게 학습이 될 경우 학습 결과에 치중되어 결과를 예측할 수 있기 때문이다. 즉, training 모델과 비교했을 때 예측 결과가 벗어나지 않지만, test 모델과 비교하면 error rate가 커진다는 것이다.

다시 말해, training 모델이 학습을 할 수록 error rate가 낮아지다가, 특정 지점에서부터 다시 error rate가 높아지기 시작하는데 이 지점이 바로 overfitting이 시작되는 지점이다. 반대로 학습이 덜 되어 test model과 training model 둘 다 예측 결과가 어긋나는 경우는 **Underfitting**이라고 한다.

![Overfitting Graph](../img/overfitting_graph.png)

#### *Overfitting 해결법 (추가예정)*
</br><br>

## Naive Bayes Classifiers
*추가예정*
</br><br>

## Regression
*추가예정*
</br><br>

## Classification
*추가예정*
</br><br>

## Neural Network
*추가예정*
</br><br>

## Reinforcement Learning
*추가예정*
