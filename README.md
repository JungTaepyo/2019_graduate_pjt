# 2019graduate_project

< 참여자 >
201302485 정태표
201402429 정진휘
201402406 이진원

파일 : noise_reduction.py 
학습 프로세스
1. 순수 기침 소리 데이터 / 소음이 섞인 기침 소리 데이터 생성
 - soundFeature() 함수
 - ./data/clean : 순수 기침 소리 음원이 있는 위치 
 - ./data/noise : 소음 음원이 있는 위치
 - 위의 두 파일을 input으로 하여 소음이 섞인 기침 소리를 만든다.
 - 해당 과정을 마치면, ./output/feature/train_feature.pickle이란 파일에 소음이 섞인 기침 소리와 순수 기침 소리의 정보를 담아 저장한다.

2.소음이 섞인 기침 소리에서 순수 기침 소리만 추출하는 딥러닝 모델 학습
 - dnn() 함수
 - 1번에서 만들어진 train_feature.pickle 파일을 읽어 소음이 섞인 기침 소리는 input data / 순수 기침 소리는 output data로 설정하여 딥러닝 모델을 학습시킨다.
 - 학습된 모델은 ./model.ckpt에 저장되어, 실제로 테스트할때 사용된다.

3.noise_reduction.py 끝에 main() 함수가 데이터 추출, 모델 학습, 테스팅

파일 : modelTesting.py
모델 테스트
1. 기본적인 파라미터 세팅 후 학습된 모델을 불러온다.
2. ./data/Test/wav 폴더 밑의 파일들로 테스트한다.
3. cvs 파일로 파일별 예측 결과를 담는다.
