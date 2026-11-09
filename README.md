# Automatic Fruit Classification Service Using AI

**English** | [한국어](#ai를-활용한-과일-자동분류-서비스)

## Project Overview & Results Summary  
This project was entered in the **2024 Hanium ICT Mentoring Contest**, hosted by the **Ministry of Science and ICT** and organized by the **Institute of Information & Communications Technology Planning & Evaluation (IITP) and the Federation of Korean Information Industries (FKII)**.  
This GitHub repository contains **the code and materials submitted to the contest**, as well as **the code used to improve performance and further develop the project after the contest**.  

In this project, we developed an **automated system** that classifies in real time whether fruit is normal, using AI models such as **YOLO, EfficientDet, and EfficientNet**.  
Using a Raspberry Pi and an Arduino, we processed the collected data in real time and visualized it as a web-based service, designing an **agricultural automation system**.  

**Results summary:**  
- **Honorable Mention** at the 2024 Hanium ICT Mentoring Contest
- Published a [paper](https://koreascience.kr/article/CFKO202433162499114.page) as co-first author at the [Korea Information Processing Society (KIPS) ACK 2024](https://www.manuscriptlink.com/society/kips/conference/ack2024) conference
- In follow-up research, carried out **AI model performance improvement** **(test accuracy improved from 25% → 76%) & improved model generalization by restructuring the data**
- The contest report and materials are in the **'2024_Hanium_ICT_mentoring_competition_and_Paper' folder** of this repository.

---

## Background  
- **Problem:** Because of population decline and aging in rural areas, the **need for automated quality control systems for agricultural products** keeps growing. Existing manual quality inspection has **limits in efficiency and accuracy**, so a technical alternative is needed.  

- **Project goals:**  
  - Develop an **AI-based fruit classification system** for **accurate quality control** and **automated productivity gains**.  
  - **Classify normal and abnormal fruit in real time** and visualize the results in a web-based service so users can monitor them easily.  

---

## **Tech Stack**

- **Language**:  
  - Python  

- **Frameworks & Libraries**:  
  - **PyTorch**: (after the contest) Design and implementation of the EfficientNet-B0 model  
  - **TensorFlow**: Design and implementation of the YOLOv5s, EfficientDet-D0, and EfficientNet-B0 models  
  - **Scikit-learn**: Data preprocessing
  - **OpenCV**: Image preprocessing and image augmentation
  - **Augmentor**: Image data augmentation (horizontal flip, brightness, contrast, color adjustment)

- **Data Processing & Analysis**:  
  - **Pandas**: Data manipulation and analysis  
  - **NumPy**: Numerical data processing and array operations
  - **Matplotlib**: Result visualization

- **Training Management & Visualization**:  
  - **Weights & Biases (wandb)**: (after the contest) Experiment and hyperparameter tuning management  

---

## Image Data Used for Model Training
- Data used for the models built during the Hanium ICT contest
  - [YOLOv5s (data from the link used as-is)](https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification)
  - [EfficientDet-D0](https://drive.google.com/drive/u/2/folders/1AotMBlR4IlhqmpxC5WBf-SbpKsxDilvy)
  - [EfficientNet-B0](https://drive.google.com/drive/u/2/folders/1tXkCgdoUun-kd0XHSJ6oGFw6jI1e00of)
- Data used for the model built after the Hanium ICT contest (**Train and Validation data built to resemble the Test dataset images**)
  - [EfficientNet-B0](https://drive.google.com/drive/u/2/folders/1Tv1ODKL3YgzKIJprE9YUsFy9Nngy-45G)

---

## Methodology (Model Selection & Data Processing)

To find the best model, this project tested **three AI models (YOLOv5s, EfficientDet-D0, EfficientNet-B0)** one after another.

### 1. Models tested during the Hanium ICT contest (in order)
- **YOLOv5s**
  - Chosen to perform object detection at the same time as fruit classification  
  - Trained on a Kaggle dataset  
  - **Issue:** Because the annotation files were not handled properly, it scored over 90% during training but detected almost no objects in actual tests  

- **EfficientDet-D0**
  - Chosen after the YOLO model, considering its **lightweight architecture and ability to run smoothly in embedded environments**  
  - Modified the data used for YOLOv5s and **restructured the dataset so that each image contains only one fruit**  
  - **Data split:** 
    - Train: 75 images/category  
    - Validation: 25 images/category  
    - Test: 25 images/category  
    - (Annotation files created manually)  
  - **Issue:** It reached high accuracy during training, but **real-world performance was poor because there was too little data overall**  

- **EfficientNet-B0**
  - **Because the project setup photographs objects with a camera, we judged that an image classification model would fit better than an object detection model, and switched to it**  
  - Expanded the dataset by **augmenting (with Augmentor)** the data used for EfficientDet-D0  
  - **Data split:**  
    - Train: 1000 images/category  
    - Validation: 800 images/category  
    - Test: 90 images/category  
  - **Results:**  
    - Recorded the highest accuracy during training and was selected as the final model  
    - **Accuracy converged to 100%** at the time of the contest submission  

### 2. Research after the contest (improving EfficientNet-B0)
- Used the contest dataset, but **rebuilt the Train and Validation sets to resemble the Test data**  
  - **To move quickly, excluded the "rotten fruit" data and kept only normal fruit (apple, banana, orange)**  
- After just one training run, **performance on the Test dataset improved from 25% → 76%**

---

## My Contribution

My main roles in this project were as follows.

### 1. Data processing & augmentation
- Performed data preprocessing and augmentation for each model: YOLOv5s, EfficientDet-D0, and EfficientNet-B0  
- Applied image augmentation such as **horizontal flips, brightness adjustment, and contrast changes** with Augmentor  
- **Augmented the dataset to over 1,000 images** to train the EfficientNet-B0 model  

### 2. Model performance analysis & improvement
- Analyzed each model's performance while moving from **YOLOv5s → EfficientDet-D0 → EfficientNet-B0**  
- After the contest, **restructured the data** to improve the EfficientNet-B0 model's performance  
  - **It scored 25% on the Test data at the time of the contest, and improved to 76% after my own research**  

### 3. Report & paper writing
- Wrote the 2024 Hanium ICT Mentoring Contest report and the [KIPS paper](https://koreascience.kr/article/CFKO202433162499114.page)  
  - Summarized the project overview and experiment results  
  - Documented the EfficientNet-B0 improvement process and results

---

# AI를 활용한 과일 자동분류 서비스

## 프로젝트 개요 & 성과 요약  
본 프로젝트는 **과학기술정보통신부**가 주최하고 **정보통신기획평가원, 한국정보산업연합회**가 주관하는 **2024 한이음 ICT 멘토링 공모전** 출품작입니다.  
이 GitHub Repository에는 **공모전에 출품했던 코드 및 자료 파일**들과 **공모전 이후 성능 개선 및 프로젝트 고도화에 사용된 코드**가 포함되어 있습니다.  

본 프로젝트에서는 **YOLO, EfficientDet, EfficientNet** 등의 AI 모델을 활용해 과일의 정상 여부를 실시간으로 분류하는 **자동화 시스템**을 개발했습니다.  
라즈베리파이와 아두이노를 사용하여 수집된 데이터를 실시간으로 처리하고, 웹 기반 서비스로 시각화하여 **농업 자동화 시스템**을 설계했습니다.  

**성과 요약:**  
- 2024 한이음 ICT 멘토링 공모전 **입선 수상**
- [한국정보처리학회 ACK 2024](https://www.manuscriptlink.com/society/kips/conference/ack2024) 학술대회에 공동제1 저자로 [논문](https://koreascience.kr/article/CFKO202433162499114.page) 게재
- 프로젝트 후속 연구로 **AI 모델 성능 개선** 진행 **(Test 데이터 성능 25% → 76% 향상) & 데이터 재구성을 통한 모델 일반화 성능 향상**
- 공모전 보고서 및 자료는 리포지토리의 **'2024_Hanium_ICT_mentoring_competition_and_Paper' 폴더**에서 확인할 수 있습니다.

---

## 프로젝트 배경  
- **문제 인식:** 농촌의 인구 감소와 고령화로 인해 **농산물 품질 관리 자동화 시스템의 필요성**이 지속적으로 증가하고 있습니다. 기존의 수작업 품질 검사는 **효율성과 정확도 측면에서 한계**가 있으며, 이를 해결하기 위한 기술적 대안이 요구됩니다.  

- **프로젝트 목표:**  
  - **AI 기반의 과일 분류 시스템**을 개발하여 **정확한 품질 관리**와 **자동화된 생산성 향상**을 도모합니다.  
  - **정상 과일과 비정상 과일을 실시간으로 분류**하고, 결과를 웹 기반 서비스로 시각화하여 사용자가 쉽게 모니터링할 수 있도록 합니다.  

---

## **기술 스택**

- **언어**:  
  - Python  

- **프레임워크 및 라이브러리**:  
  - **PyTorch**: (공모전 이후)EfficientNet-B0 모델 설계 및 구현  
  - **TensorFlow**: YOLOv5s, EfficientDet-D0, EfficientNet-B0 모델 설계 및 구현  
  - **Scikit-learn**: 데이터 전처리
  - **OpenCV**: 이미지 전처리 및 이미지 파일들의 증강에 사용
  - **Augmentor**: 이미지 데이터 증강(좌우 대칭, 밝기, 대비, 색상 조절)

- **데이터 처리 및 분석**:  
  - **Pandas**: 데이터 조작 및 분석  
  - **NumPy**: 수치 데이터 처리 및 배열 연산
  - **Matplotlib**: 결과 시각화

- **모델 학습 관리 및 시각화**:  
  - **Weights & Biases (wandb)**: (공모전 이후)실험 및 하이퍼파라미터 튜닝 관리  

---

## 모델 학습에 사용된 이미지 데이터 파일들
- 한이음 ICT 공모전 당시 제작했던 모델들에 쓰인 데이터
  - [YOLOv5s(링크의 데이터 그대로 사용)](https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification)
  - [EfficientDet-D0](https://drive.google.com/drive/u/2/folders/1AotMBlR4IlhqmpxC5WBf-SbpKsxDilvy)
  - [EfficientNet-B0](https://drive.google.com/drive/u/2/folders/1tXkCgdoUun-kd0XHSJ6oGFw6jI1e00of)
- 한이음 ICT 공모전 이후 제작한 모델에 쓰인 데이터(**Test 데이터셋의 이미지와 유사하도록 Train, Validation 데이터를 구성**)
  - [EfficientNet-B0](https://drive.google.com/drive/u/2/folders/1Tv1ODKL3YgzKIJprE9YUsFy9Nngy-45G)
 
---

## 방법론 (Model Selection & Data Processing)

본 프로젝트에서는 최적의 모델을 찾기 위해 **3가지 AI 모델(YOLOv5s, EfficientDet-D0, EfficientNet-B0)**을 순차적으로 실험하였습니다.

### 1. 한이음 ICT 공모전 당시 실험한 모델들 (순차적으로 실험 진행)
- **YOLOv5s**
  - 과일을 분류하면서 동시에 객체 인식까지 수행하고자 선택  
  - Kaggle 데이터셋을 활용하여 모델을 학습  
  - **문제점:** Annotation 파일의 처리가 미흡하여 학습 과정에서는 90% 이상의 성능을 기록했으나, 실제 테스트에서는 물체를 거의 인식하지 못함  

- **EfficientDet-D0**
  - YOLO 모델 이후에 선택한 모델로, **경량화된 구조와 임베디드 환경에서의 원활한 구동 가능성**을 고려하여 채택  
  - YOLOv5s에서 사용한 데이터를 수정하여, **이미지 1장당 1개의 과일만 포함되도록 데이터셋을 재구성**  
  - **데이터 구성:** 
    - Train: 75장/카테고리  
    - Validation: 25장/카테고리  
    - Test: 25장/카테고리  
    - (수동으로 Annotation 파일 제작)  
  - **문제점:** 모델 학습 과정에서는 높은 정확도를 기록했으나, **절대적인 데이터 수 부족으로 인해 실제 성능이 저조**  

- **EfficientNet-B0**
  - **프로젝트 환경에서 카메라로 물체를 촬영하는 방식이 사용되었기 때문에, 객체 인식 모델이 아닌 이미지 분류 모델이 더 적합하다고 판단하여 전환**  
  - EfficientDet-D0에서 사용한 데이터를 **증강(Augmentor 적용)** 하여 데이터셋을 확장  
  - **데이터 구성:**  
    - Train: 1000장/카테고리  
    - Validation: 800장/카테고리  
    - Test: 90장/카테고리  
  - **결과:**  
    - 모델 학습 중 가장 높은 정확도를 기록하여 최종 모델로 선정  
    - 공모전 제출 당시 **정확도 100% 수렴**  

### 2. 공모전 이후 진행한 연구 (EfficientNet-B0 성능 개선)
- 공모전 당시의 데이터셋을 활용하되, **Test 데이터와 유사한 Train 및 Validation 데이터셋 재구성**  
  - **빠른 진행을 위해 "썩은 과일" 데이터는 제외하고 정상적인 과일(사과, 바나나, 오렌지)만 포함**  
- 모델 학습 1회 시행만에 **Test 데이터셋에서 성능이 25% → 76%로 향상**

---

## 개인 기여 (My Contribution)

본 프로젝트에서 담당한 주요 역할은 다음과 같습니다.

### 1. 데이터 처리 및 증강
- YOLOv5s, EfficientDet-D0, EfficientNet-B0 모델별 데이터 전처리 및 증강 수행  
- Augmentor를 활용하여 **좌우 반전, 밝기 조정, 대비 변경** 등의 이미지 증강 적용  
- EfficientNet-B0 모델의 학습을 위해 데이터셋을 **1,000장 이상 증강**  

### 2. 모델 성능 분석 및 개선
- **YOLOv5s → EfficientDet-D0 → EfficientNet-B0** 모델 변경 과정에서 각 모델의 성능을 분석  
- 공모전 종료 후 EfficientNet-B0 모델의 성능을 개선하기 위해 **데이터 재구성** 수행  
  - **공모전 당시 Test 데이터에서 25%의 성능을 보였으나, 개인 연구 진행 후 76%까지 개선**  

### 3. 보고서 & 논문 작성
- 2024 한이음 ICT 멘토링 공모전 보고서 및 [한국정보처리학회 논문](https://koreascience.kr/article/CFKO202433162499114.page) 작성  
  - 프로젝트 개요 및 실험 결과 정리  
  - EfficientNet-B0 성능 개선 과정 및 결과 정리
