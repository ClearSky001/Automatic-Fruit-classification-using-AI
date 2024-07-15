# Automatic Fruit Classification using AI

모델을 몇 가지 제작하여, 그 중 성능이 가장 좋은 모델로 과일 분류기를 제작하는 프로젝트입니다.

## 프로젝트를 수행하며 제작한 모델들

### 1. YOLOv5s 모델

#### 모델 제작에 사용된 데이터셋

모델 훈련 및 모델 테스트에 사용된 데이터셋은 다음 경로에서 다운로드할 수 있습니다: [Kaggle 데이터셋](https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification)

#### 모델 제작 및 Test 데이터셋을 통해 모델의 성능 측정의 전 과정
(YOLOv5s_model_train_and_model_test.ipynb 파일 참고)

GitHub에서 YOLOv5s_model_train_and_model_test.ipynb 파일이 열리지 않고 있습니다. 해당 파일을 다운로드한 후 Jupyter Notebook에서 열면 출력값들이 잘 나옵니다.

#### YOLOv5s 모델의 전반적 성능 및 실제 환경에서의 테스트

yolov5s_model_test_result_data 폴더에서 확인할 수 있듯, 상당히 높은 성능을 보입니다.
* 실제 과일 사진을 직접 찍어 모델에 인식시키고 웹캠에 과일을 가져다 대어 모델이 실제 환경에서도 잘 작동하는지를 테스트하였습니다. 테스트 데이터에서 높은 정확도를 보였던 모델이 실제 환경에서는 과일을 제대로 인식하지 못하는 경우가 발생하였습니다.

  * 해결 방안:
    1. **검증 데이터 추가**:
       인공지능 모델 구축에는 학습 데이터와 테스트 데이터뿐만 아니라 검증 데이터(Validation Data)도 필요합니다. 검증 데이터는 모델이 학습하는 동안 주기적으로 모델의 성능을 평가하여 과적합(overfitting)을 방지하는 역할을 합니다. 검증 데이터를 추가하여 다시 학습을 진행할 계획입니다.

    2. **하이퍼파라미터 튜닝**:
       학습률, 배치 크기 등의 하이퍼파라미터를 조정하여 모델의 성능을 최적화합니다.

    3. **전이학습**:
       사전 학습된 모델을 사용하여 전이 학습을 수행하여 적은 양의 데이터로도 높은 성능을 달성하게 만듭니다.

## 프로젝트 사용법

1. 저장소 클론:
   ```bash
   git clone https://github.com/ClearSky001/Automatic-Fruit-classification-using-AI.git
