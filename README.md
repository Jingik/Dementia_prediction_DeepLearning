👋 들어가며

본 포스팅은 `조기 치매 예측 프로젝트`로 AIhub에서 제공받은 데이터를 활용해 다양한 딥러닝 기술로 연구한 프로젝트입니다.

📚 목차
>
**1. 프로젝트 소개
2. 수행기간
3. 프로젝트 흐름도
4. 수행 과정
5. 수행 결과
6. 기대효과 활용분야
7. 한계점 및 향후 개선 방향
8. 참고자료**

## 🔎 1. 프로젝트 소개 

**Wearable-based Lifelog Data Prediction for Dementia**


본 프로젝트는 웨어러블 기반 라이프로그 데이터를 활용하여 치매 예측 성능을 향상시키기 위해 다 양한 접근 방식을 탐색하고, 이후 나온 결과를 바탕으로 성능을 높이기 위해 새로운 데이터 생성, 딥러닝 모델 개발 등을 실행한다.


 
- **프로젝트 달성 목표**
제공받은 라이프로그 데이터와 다양한 딥러닝 모델을 이용해 최상의 결과를 도출하고, 이를 토대로 `치매 예측 모델의 개발과 활용`에 기여하고자 합니다.  

- **필요성 및 기대효과**
2020년 기준, 65세 이상의 노인 인구 중에서 10% 이상이 치매를 겪고 있으며, 경도 인지 장애와 같은 치매의 초기 단계에 해당하는 질환이 60세 기준으로 20% 이상인 것으로 알려져 있습니다. 치매는 국가적으로도 큰 피해를 주는데 뿐만 아니라 가정 내에서도 큰 영향을 미치기 때문에 이 문제를 꼭 해결해야 합니다. 그러나 현재 치매를 측정하기 위한 방법은 매우 어렵고 비용도 많이 들어가기 때문에 현실적으로 어렵습니다. 따라서, 웨어러블 기반 데이터 수집을 통해 별도의 시간을 투자하지 않고도 수집된 데이터를 기반으로 치매와 경도 인지 장애를 조기에 예측을 가능하게 해 시간과 금액에서 모두 이익을 보려고 합니다.  
<br>

## 📔 2. 프로젝트 수행기간

![](https://velog.velcdn.com/images/jingit/post/ae7381df-c3dc-4ecb-8d26-c9ef0b8de038/image.png)

[Github 주소]<https://github.com/Jingik/Dementia_prediction_DeepLearning.git>
<br>

## 📌 3. 프로젝트 흐름도
![](https://velog.velcdn.com/images/jingit/post/77e768cd-bc7e-4b29-af16-412cbc076254/image.png)


<br>

## 📌 4. 프로젝트 수행과정
### 1) 전처리 단계 : 결측치 처리
![](https://velog.velcdn.com/images/jingit/post/e13059f7-915d-4212-8641-cdd4a91a6479/image.png)


- 결측치 처리
- 사용하지 않는 변수 삭제


### 2) 전처리 단계 : 데이터 스케일링
![](https://velog.velcdn.com/images/jingit/post/65945fd7-c078-44b7-b29c-505613192971/image.png)


- 좌측 편향 데이터 - ** Log Transform **
- 우측 편향 데이터 - ** Quantile Transform**
- 그 외의 데이터 - ** RobustScaler **

### 2) 전처리 단계 : RandomForest와 차원축소를 이용한 데이터 생성

![](https://velog.velcdn.com/images/jingit/post/5f02f110-5462-4431-8884-d03831ffde48/image.png)

- Randomfores를 이용해 변수 중요도별 그룹 생성
- 해당 그룹의 변수들을 PCA를 통해 각각의 그룹 별 변수로 생성

### 2) 전처리 단계 
#### 1. 라이프로그 시그널 데이터 그래프로 변형

![](https://velog.velcdn.com/images/jingit/post/2f235451-cbca-4308-a747-2bb72d2b6619/image.png)

- 공공 데이터로 제공받은 시계열 데이터를 그래프 형태로 변형

#### 2. 임의의 Resnet + VAE 모델을 이용해 변수 생성
![](https://velog.velcdn.com/images/jingit/post/a9734971-d98c-4a8c-b9e1-aae3238f9e47/image.png)


- AutoEncoder의 특징인 압축과 풀기 과정에서 생성되는 Latent Vector 데이터 활용

#### 3. VAE 모델을 이용한 변수 생성
![](https://velog.velcdn.com/images/jingit/post/6e2a461d-63f3-46f6-8acf-2f8930269cc9/image.png)


- AutoEncoder의 특징인 압축과 풀기 과정에서 생성되는 Latent Vector 데이터 활용

### 3) 딥러닝 모델 구현
#### 1. LSTM 앙상블 모델 구현

![](https://velog.velcdn.com/images/jingit/post/c0e310f9-5a26-448b-a0b8-627fcf4cf909/image.png)


- Keras를 이용해 Model 구현

#### 2.CNN + LSTM 모델 구현
![](https://velog.velcdn.com/images/jingit/post/ab0e8599-3937-42c2-b3cc-0a0694a4cb9e/image.png)


- Keras를 이용해 Model 구현

#### 3. ResNet 모델 구현
![](https://velog.velcdn.com/images/jingit/post/5ea9a3db-aa09-4d18-8e54-442554094c27/image.png)


- Keras를 이용해 Model 구현


## 📌 5. 수행 결과
> 
**Case 1. (Resnet+Vae_Latenet) + (Randomforest + PCA) + Processed Data **

![](https://velog.velcdn.com/images/jingit/post/8ced79fe-d09a-4be3-9178-d61d915beee6/image.png)


> 
**Case 2. Vae_Latenet + (Randomforest + PCA) + Processed Data **

![](https://velog.velcdn.com/images/jingit/post/3f252ff4-e5ce-4d41-8d51-573a77ef4ec1/image.png)


> 
**Case 3. (Resnet+Vae_Latenet) + Processed Data**

![](https://velog.velcdn.com/images/jingit/post/c169b3d8-6d8b-4e0c-beec-b1feaccf7897/image.png)


> 
**Case 4. Processed Data**

![](https://velog.velcdn.com/images/jingit/post/355942dc-fffc-4667-bef2-e6cdfe0534fe/image.png)

- 웨어러블 기반 라이프로그 데이터를 활용하여 치매 예측을 수행하는 것은 유효하며, 딥러닝 모델을 활용할 때 높은 예측 성능을 얻을 수 있었습니다. 특히, LSTM 앙상블과 ResNet 모델은 뛰어난 성능을 보여주었습니다.

- 생체 신호 데이터를 이용해 얻은 Latent Vector가 성능을 높이는데 기여했음을 알 수 있습니다. 이를 통해 사람의 하루 싸이클 생체신호 데이터를 통해 더 정확한 예측이 가능함을 알 수 있습니다.

- 변수 중요도에 따른 PCA 작업이 성능을 높이는데 기여함을 알 수 있습니다. 특히, 재현율 측면에서 잠재 변수와 차원 축소 변수의 합성이 높은 성능을 보였습니다. 


<br>

## ✏️ 6. 기대효과 및 활용 방안

- **기대효과**
해당 프로젝트를 통해 웨어러블 라이프로그 데이터를 이용한 치매 예측이 유효하며 해당 기술이 더 발전한다면 사회적과 경제적인 측면에서 많은 효과를 보일 수 있을 것이라고 기대합니다.

- **활용분야**
해당 프로젝트를 통해 웨어러블 라이프로그 데이터가 단순히 사람의 심박수 같은 것만 재는 것이 아닌 치매예측, 더 나아가 다양한 질병예측에도 쓰일 수 있을 것이라고 기대합니다.

<br>


## 🔨 7. 한계점 및 향후 개선 방안
**- 데이터의 부족**

공공데이터를 활용하면서, 특히 사람의 개인정보가 포함된 데이터의 한정적인 확보로 인해 과적합과 같은 결과가 나타난 것으로 보입니다. 이러한 상황에서는 데이터의 양적 부족으로 인한 모델의 성능 하락이 발생할 수 있습니다. → 데이터의 부족함을 보완하기 위해 SMOOTH와 같은 방법을 고려하여 데이터를 증가시켜 일반화 성능을 높이고자 함.


**- 데이터 분석의 미흡 **

데이터 EDA을 통한 데이터의 특징으로 Scaling 처리를 진행함 → 데이터를 더 정교하게 비교하거나 LSTM 모델을 활용하여 중요한 데이터를 추출함으로써, 과적합을 방지하고 모델의 일반화 성능을 높이고자 함.


<br>

## 📜 8. 참고자료

- Harold Hotelling, "Analysis of a Complex of Statistical Variables into Principal Components," Journal of Educational Psychology, Vol. 24, No. 7, pp. 498-520, 1933.

- Box, G. E. P., & Cox, D. R. (1964). An analysis of transformations. Journal of the Royal Statistical Society: 
Series B (Methodological), 26(2), 211-252.

- R.J. Hyndman and Y. Fan, "Sample Quantiles in Statistical Packages," The American Statistician, Vol. 50, No. 4, pp. 361-365, 1996.

- Rousseeuw, P.J., Croux, C. (1993). Alternatives to the Median Absolute Deviation. Journal of the American Statistical Association, Vol. 88, pp. 1273-1283.

- Leo Breiman, "Random Forests," Machine Learning, Vol. 45, No. 1, pp. 5-32, 2001.

- Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun. "Deep Residual Learning for Image Recognition", Proceedings of the IEEE conference on computer vision and pattern recognition, pp. 770-778, 2016.

- Diederik P Kingma, Max Welling. "Auto-Encoding 
Variational Bayes", International Conference on Learning Representations, 2014.

- Hochreiter, S., & Schmidhuber, J. (1997). Long short-term memory. Neural computation, 9(8), 1735-1780.

- LeCun, Y., Bottou, L., Bengio, Y., & Haffner, P. (1998). Gradient-based learning applied to ocument recognition. Proceedings of the IEEE, 86(11), 2278-2324.





