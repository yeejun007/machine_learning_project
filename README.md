machine_learning_project
========================


#### 팀 구성
송이준, 이진주, 조대선

####
2020.04.23 ~ 2020.05.30

# 


### Goals
#### bare minimum
 딥러닝 모델을 이용하여 웹툰 작가이름 맞추기
#### advanced
 비슷한 그림체의 웹툰 찾아내기


### Technical Skills
- python, tensorflow(keras), google colab

#


### Plan
1. 이미지 수집 (네이버, 다음의 연재중인 웹툰)
2. 네이버 웹툰 중, 썸네일 이미지 200개 이상인 웹툰들 선별 (총 33개)
3. colab GPU를 사용하여, keras로 모델링 진행



### model
 <img width="1075" alt="스크린샷 2020-05-22 오후 1 19 36" src="https://user-images.githubusercontent.com/46306443/82630884-0042df80-9c2f-11ea-9a1f-d54eb7c0e9e4.png">
 

### Details
1. 연재중인 모든 웹툰을 메모리에 올릴 수 없다 (colab 가용 메모리 : 25GB)
2. MINST 손글씨 분류 모델에서, 숫자(라벨) 하나당 이미지 갯수가 6000개 였음을 감안하여 웹툰 하나당 이미지 갯수가 최소 10,000개는 되어야 겠다고 생각함
   -> 네이버 웹툰 중, 썸네일 200개 이상인 웹툰만 선별(33개)해서 augmentation으로 각 라벨당 이미지 갯수 50배로 증가시킴 ->
3. 전체 Dataset을 train_data, validation_data, test_data로 나눔
4. accuracy 향상 
- filter 갯수 증가, filter 갯수 증가 방식 변경(점차적 증가)
- layer 깊이 증가
5. 과적합 해소 (train_accuracy와 validation_accuracy의 격차 감소시키기)
- regularization layer를 매번 사용
- droupout layer 추가 (0.2~0.6비율로 점차적으로 증가시키면서 적용)
6. 









