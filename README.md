# Automatic Fruit Classification using AI
모델을 몇 가지 제작하여, 그 중 성능이 가장 좋은 모델로 과일 분류기를 제작하는 프로젝트입니다.
* 프로젝트를 진행하는 동안 GitHub에 지속적으로 업데이트해 나갈 예정이며, 프로젝트가 종료된 후에는 이 README를 영어로도 번역하여 게재할 계획입니다.(I will continue to update GitHub page as we proceed with the project, and I'm planning to translate this README into English after the project is completed. So stay tuned!😊)

## 💡 About this project
이 프로젝트는 한국의 과학기술정보통신부에서 주최하고, 한국정보산업연합회(FKII)에서 주관하는 프로젝트입니다.

#### This project is part of 'Hanium ICT mentoring(https://www.hanium.or.kr/portal/index.do)', which is hosted by Korea's Ministry of Science and ICT and organized by the Federation of Korean Information Industries (FKII).

## 📚 프로젝트를 수행하며 제작한 모델들(AI Models which I've used and built during this project)

### 1. YOLOv5s 모델

* #### 모델 제작에 사용된 데이터셋
모델 훈련 및 모델 테스트에 사용된 데이터셋은 다음 경로에서 다운로드할 수 있습니다: [Kaggle 데이터셋](https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification)

* #### 모델 제작 및 Test 데이터셋을 통해 모델의 성능 측정의 전 과정
(YOLOv5s_model_train_and_model_test.ipynb 파일 참고)

GitHub에서 YOLOv5s_model_train_and_model_test.ipynb 파일이 열리지 않고 있습니다. 해당 파일을 다운로드한 후 Jupyter Notebook에서 열면 출력값들이 잘 나옵니다.

 * #### Algorithm I used while labeling the .txt file of each Test & Train images :
  
   * #### I used Otsu algorithm for YOLOv5s model to detect the images

### YOLOv5s 모델의 Test 데이터셋에서의 전반적 성능

yolov5s_model_test_result_data 폴더에서 확인할 수 있듯, 상당히 높은 성능을 보입니다. 아래의 이미지들은 모델 훈련 뒤, Test 데이터셋으로 측정한 모델의 성능 지표들입니다. 위에서부터 순서대로 Confusion Matrix, F1-Confidence Curve, Precision-Confidence Curve, Precision-Recall Curve, Recall-Confidence Curve, 그리고 6개의 항목에 대한 모델의 성능 지표를 시각화한 결과입니다.

![Confusion Matrix](images/confusion_matrix.png)
![F1-Confidence Curve](images/F1_curve.png)
![Precision-Confidence Curve](images/P_curve.png)
![Precision-Recall Curve](images/PR_curve.png)
![Recall-Confidence Curve](images/R_curve.png)
![Visualization of yolov5s model test result](images/visualization_of_yolov5s_model_test_result.PNG)

* ### 💥 Problem & Issues

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
