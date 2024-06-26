# 취업준비생 서류 합격/불합격 예측 시스템


## 프로젝트 개요
이 프로젝트는 취업준비생의 스펙(학점, 학력, 자격증, 해외경험, 인턴 경험 등)을 기반으로 특정 직무나 회사의 합격 가능성을 예측하는 머신러닝 기반 시스템을 개발하는 것입니다. 이 시스템은 취업준비생들에게 현실적인 평가와 피드백을 제공하여 취업 준비 과정을 효율적으로 개선할 수 있도록 돕습니다.
### 목적
  - 취업 준비 효율화: 취준생들이 자신의 스펙에 대한 객관적인 평가를 받고, 기업이 어떤 스펙을 중요시하는지에 대한 파악을 하며 합격 가능성을 높일 수 있는 구체적인 조언을 제공받습니다.

### 기능
  - 스펙 입력: 사용자가 자신의 학력, 경력, 자격증, 인턴 경험 등의 정보를 입력합니다.
  - 합격 가능성 예측: 입력된 데이터를 기반으로 머신러닝 모델이 특정 직무나 회사에 대한 합격 가능성을 예측합니다.


## 필요한 라이브러리(버전) 또는 프로그램 목록 
  * pandas: 2.0.3 
  * scikit-learn: 1.2.2
  * numpy: 1.25.2
  * matplotlib: 3.7.1


## 프로젝트 과정 중 핵심
* 프로젝트 과정에서 스펙 항목들을 보다 균형있게 조정하기 위해서 정규화한 후, 상관관계 분석을 통해 이 항목들 간의 관계를 명확하게 파악했습니다. 이를 통해 주요 변수들이 서로 어떻게 연관되어 있는지 이해할 수 있었고, 데이터의 패턴과 통찰을 도출할 수 있었습니다.


__정규화__
![정규화](https://github.com/hyoryeomii/job-seeker/blob/main/%EC%A0%95%EA%B7%9C.png)


__상관관계 분석 표__
  ![상관관계](https://github.com/hyoryeomii/job-seeker/blob/main/%EC%83%81%EA%B4%80%EA%B4%80%EA%B3%84.png)


## 추후 개선 사항 및 한계점 
1. 더 많은 항목 수집
  * 목표: 다양한 항목(예: 프로젝트, 전공학점 등)을 포함하여 예측 모델의 정확도를 높이기 위해 더 많은 데이터를 수집하려고 노력했습니다.
  * 한계: 데이터 수집의 한계로 인해 일부 중요한 항목을 포함하지 못했습니다. 이는 모델의 예측 성능과 결과의 신뢰도에 영향을 미칠 수 있습니다.
2. 자기소개서 평가
  * 목표: 현대 채용 과정에서는 서류 전형보다 자기소개서의 비중이 더 높아지는 추세를 반영하려 했습니다.
  * 한계: 서류를 아예 고려하지 않는 것은 아니지만, 자기소개서 데이터를 충분히 확보하지 못해 이를 모델에 포함시키는 데 어려움이 있었습니다. 따라서 서류 항목에 초점을 맞춘 모델로 제한되었습니다.
3. 피드백 제공
  * 보다 더 나은 취업 도움을 주기 위해 항목 중 어느 부분이 부족한지에 대한 피드백 제공을 하는 서비스도 추가하고싶습니다.
4. 랜덤 포레스트 이외에 머신러닝 다른 모델 사용
  * 이진분류 문제 강력하며 높은 정확도를 제공하는 __서포트 벡터머신__, 이진분류 문제에 매우 간단하고 강력한 선형결합 사용하는 __로지스틱회귀__, 인스턴스기반하여 새로운 데이터 포인트 클래스 결정을 위해 가까운 이웃들의 레이블 기반 복잡한 데이터 패턴에 좋은 __KNN__, 여러개 결정 트리 학습하여 약한 학습자를 강한 학습자로 결합하고 불균형한 데이터셋에 효과적인 __Gradient boosting__ 을 사용해보고싶습니다. 


## 데이터 세트: 데이터셋에 대한 설명 및 출처

__아래와 같은 사이트에서 직접 수집하여 데이터를 생성했습니다.__
* 잡코리아
https://m.jobkorea.co.kr/company/1795098/passavgspec?Page=1&IsAlumniPersonOn=0&Tab=3&IsFavorOn=0&IsAlumniOn=0&VPage=1


* 독취사
https://cafe.naver.com/dokchi


## 모델 설명
* __랜덤포레스트__

처음에는 랜덤 포레스트를 머신러닝에서 매우 널리 사용되는 기본적인 모델 중 하나이기 때문에 사용했었는데, 높은 예측 정확도의 결과가 계속 나오고 데이터의 변동이 있어도 안정적인 성능을 유지하는 특징 때문에 이후에 쭉 사용했습니다.


## 모델 평가에 사용된 지표와 결과
* F1-score, Recall, Precision, Accuracy
  ![그래프이미지](https://github.com/hyoryeomii/job-seeker/blob/main/%ED%91%9C.png)


## 나의 합격 확률은?!?(구현해보기)

* 확률에서 0.4: 불합격 확률, 0.6: 합격 확률입니다.
* 학점 (30점 = 4.0-4.5, 25점 = 3.0-3.5, 15점 = 2.5-3.0, 5점 = 3.0 미만)
![구현](https://github.com/hyoryeomii/job-seeker/blob/main/%EA%B5%AC%ED%98%84.png)
