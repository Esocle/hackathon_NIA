# hackathon_NIA

가축(젖소, 돼지) 발정 탐지를 위한 행동식별 AI 모델개발 해커톤

▪ 공개된 학습데이터 셋을 통해 젖소/ 돼지 축종 각각에 대한 결과 1,2를 도출
- 결과 1) Keypoint mAP50
- 결과 2) Pose classification (F1-score)

사용 모델 : keypoints rcnn

dataset 공개 불가


1. 이미지 데이터 확보
 * 경진대회서 제공된 keypoint 좌표가 찍힌 젖소, 돼지 데이터 확인
 (돼지 8개, 젖소 13개)
 - 각 개체들의 라벨 확인 (lying, eating 등)

2. 데이터 전처리
 - keypoint 좌표값과 다른 정보들이 있는 json 파일을 RCNN모델에서 학습하기위해
 좌표값들만 선정해 csv 파일로 변환

3. 키포인트 추출 모델 학습
 - keypoint 값들만 저장된 csv 파일을 통해 RCNN 모델로 학습

4. 라벨 분류 모델
 - 기존의 제공된 train 데이터의 keypoint 값들을 x data로 놓고
 y data는 각 키포인트에 해당 라벨들로 지정
 - sklearn의 randomForestClassifier 활용하여 학습

5. 결과값 도출
 - 테스트 이미지를 학습시킨 RCNN 모델에 넣어 Keypoint 값 추출
 - 추출한 keypoint값을 학습시킨 라벨 분류모델에 넣어 해당하는 keypoint의
 라벨링 값 추출
 - 최종 결과값으로 keypoint와 라벨을 json 파일형식으로 변형

© 2022 Esocle <shbae1207@gmail.com>
