# DeepFM - part 1

---

- 관련 영상

[https://www.youtube.com/watch?v=zxXRGhSQ1f4&list=PLfhWYXHycS2RD-yuoyNOT8HBQ9PBfRl3J&index=5](https://www.youtube.com/watch?v=zxXRGhSQ1f4&list=PLfhWYXHycS2RD-yuoyNOT8HBQ9PBfRl3J&index=5)

---

- 관련 논문

[](https://github.com/hongleizhang/RSPapers/blob/master/10-CTR_Prediction_for_RS/2017-A%20Factorization-Machine%20based%20Neural%20Network%20for%20CTR%20Prediction-arXiv.pdf)

---

- 관련 키워드

FM : 모델, 선형모델

ctr task: 클릭 횟수 확률, 데이터

matrix factorization : 모델

vae-cf : 모델

cold start , exploration : 기존 모델의 문제점?

WideAndDeep : 모델(단순히 몇겹 쌓아놓은 ANN에 불과하지만 꽤 성능이 좋다고 한다.) (= LR & DNN)

CTR Prediction Model : 모델?, 모델의 추구 방향성?(소비 이력이 없어도 작동해야 한다.// 광고주들을 위해 어쩔 수 없다.)

Recommendation Model : 모델?, 모델의 추구 방향성?

data fields : click 여부, like 여부, display(광고 노출 시간)

outbrain ctr prediction challenge : 대회 이름

outbrain : 인터넷 광고 회사(광고주와 소비자 사이 중개인??)

FFM : 모델(FM과 달리 가중치가 어떤 필드와 상호작용하느냐에 따라 차별화됨????)

DeepFM : 모델( WideAndDeep + FM ??? )

NormDNN : 최신 모델 (DeepFM based)

DeepLight : 최신 모델 (DeepFM based)

DKT : 모델?

- 간단한 정리

기존 추천 모델 형식

1. Matrix Factorization Model
    
    User-interaction data를 바탕으로 추천
    
2. VAE-CF
    
    Encoder/Decoder, VAE를 통해 user의 과거 취향 분석 & 추천 
    
    특정확률로 random item을 뽑아 exploration probelm을 해결 (cold start: 기존데이터가 없는 새로운 정보)
    

CTR Prediction Model (Binary Classification Model)

- CTR: Click Through Rate

- User가 무엇인가에 노출되었을때 클릭할 확률 (feature이 미리 지정되지 않음 - 그때그때 달라지기 때문)

- Binary Cross-Entropy와 Metadata를 많이 사용 (새로운아이템을 자동으로 추천) 

Recommendation Model

- 각 user 당 전체 item의 probability를 계산 (과거 소비로서 부터)

* CTR과 Rec. 모델은 각각 서로의 상황에 쓰이기도 한다. 

Factorization Model (FM)

- ML, 각 feature들간의 interaction 을 다루는 linear model

- Binary(Yes/No) = Entropy(∀ 카테고리 field combination)

Field-aware Factorization Model (FFM)

- FM에서 각 카테고리별로 weight를 추가 

Wide and Deep learning

- Deep: (Continuous feature + Categorical feature) 을 MLP 를 통해 학습

- Wide: 임의의 2 가지의 cross-product tranformation

Wide 과 Deep에서 나온것을 잘 합쳐서 output으로...

DeepFM

- Wide and Deep learning에서 Wide 대신 FM을 사용하는것 

- AUC와 log loss 를 사용하는 이유? 

- Rec. Sys. 는 한가지의 best probability를 요구하지만, CTR은 결국 모든 아이템들의 probability 가 필요하기 때문

최신 DeepFM 사용한 model & study

- NormDNN
    - DeepFM의 MLP에 layer-norm을 추가하였다 (어떤 norm이 좋을지 등을 다루기도함)
- DeepLight
    - Pruning, Feature interaction search 등을 추가하였다 (상당히 빨라지고 퀄리티도 좋아졌다)