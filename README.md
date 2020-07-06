machine_learning_project
========================


#### 팀 구성
송이준, 이진주, 조대선

####
2020.04.23 ~ 2020.05.28

# 
<br/>

### `Goal`
비슷한 그림체의 웹툰 찾아내기
<br/>

### `Technical Skills`
- python, tensorflow(keras), google colab
<br/>

### `Procedure`
1. 이미지 수집 (네이버, 다음의 연재중인 웹툰)
2. 네이버 웹툰 중, 썸네일 이미지 200개 이상인 웹툰들 선별 (총 33개)
3. colab GPU를 사용하여, tensorflow(keras)로 모델링 진행
<br/>
<br/>

## `Project Info`

### model description
<br/>

 ![image](https://user-images.githubusercontent.com/46306443/83099196-a5563000-a0e7-11ea-9868-f2811163d3e1.png)
 
<br/>
<br/>

### issue
1. 그림체 분류를 위한 라벨링 문제('그림체'라는 것에 대해 분류 가능한 일반적인 정의가 없다.)
2. 데이터의 개수 부족 문제
3. 각 라벨에 속한 데이터 개수의 편차가 심하다 (연재 횟수가 5회 미만인 웹툰 / 현재 횟수가 1000회 이상인 웹툰)
4. 연재 중인 모든 웹툰에 대해 agumentation을 수행하면, 메모리에 한번에 올릴 수 없다. (colab 가용 메모리 : 25GB)
5. Modeling을 계속해도 과적합 문제가 완전히 해결되지 않는 문제
<br/>
<br/>

### issue solving
1. 그림 작가마다 그림체가 다를 것이라고 가정하고, 그림 작가 이름을 라벨로 사용한다. (이미지는 웹툰 각 회차의 썸네일 이미지를 사용함)

   <img width="600" alt="스크린샷 2020-05-28 오후 2 36 04" src="https://user-images.githubusercontent.com/46306443/83102928-a475cc00-a0f0-11ea-94fb-2c6b9eab7794.png">
   <br/>

2. accuracy가 90%가까이 나오는 MNIST 숫자 분류 CNN모델을 보면, 숫자 라벨 하나당 최소 6000장의 이미지가 있어야 한다.
   이미지 augmentation을 통해 각 라벨당 이미지 개수가 최소 10,000장이 되도록 한다.
   
   <img width="600" alt="스크린샷 2020-05-28 오후 2 36 17" src="https://user-images.githubusercontent.com/46306443/83102980-bc4d5000-a0f0-11ea-8bd2-60bb80f5c57f.png">
   <br/>
   
3. 현재 연재 중인 웹툰 중에, 연재 회차가 200회 이상인 웹툰들만 선별한다.
<br/>

4. 연재 회차가 200회 이상인 웹툰을 선별한 뒤에, 이미지 사이즈를 35*21로 줄여서 학습 데이터로 사용한다.(이미지의 해상도 조절)
   
   <img width="600" alt="스크린샷 2020-05-28 오후 2 46 07" src="https://user-images.githubusercontent.com/46306443/83103601-fb2fd580-a0f1-11ea-8619-d96746b1a53f.png">
   <br/>

5. dropout의 파라미터를 크게 적용시킨 layer를 추가해서 training accuracy를 낮춘다. validation accuracy도 조금 낮아지지만, train과 validation의 격차 해소를 통해 좀더 모델을 일반화 할수 있게 됨으로써 얻게 되는 이득이 더 크다고 판단 함

   <img width="800" alt="스크린샷 2020-05-28 오후 2 50 51" src="https://user-images.githubusercontent.com/46306443/83103930-ac367000-a0f2-11ea-8045-37bf6a9e3542.png">
<br/>
<br/>

### result

테스트로 사용할 이미지를 input data로 넣으면, model이 그 input data가 각 라벨에 속할 확률을 리턴해준다.
model이 가장 유사하다고 하는 작가명에 해당하는 웹툰 top10을 선별해서 보여준다.
(아래 그림은 '유미의 세포들' 웹툰 작가를 93% 확률로 맞추는 것을 보여준다)

<img width="960" alt="스크린샷 2020-05-28 오후 2 58 56" src="https://user-images.githubusercontent.com/46306443/83104459-c45abf00-a0f3-11ea-8441-b1454c608132.png">
<br/>
<br/>










