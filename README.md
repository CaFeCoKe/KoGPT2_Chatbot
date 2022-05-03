# KoGPT2_Chatbot

## - 알고리즘 순서도<br><br>


## - GPT(Generative Pre-trained Transformer) 구성<br><br>


## - 결과
 + 데이터 로더<br><br>
![dataloader](https://user-images.githubusercontent.com/86700191/166405695-ef706aee-5304-4799-85d4-ca397eef806e.PNG) <br>
어떤 인덱스 텐서인지 알아보기 쉽게 출력이 되어있다. 데이터 로더에는 이름은 없이 텐서만 들어간다.
<br><br>
 + 학습시 손실 값<br><br>
![loss](https://user-images.githubusercontent.com/86700191/166406370-fa059d78-4a83-4707-b6f4-9ed4a14fb5be.PNG) <br>
결과가 아니라 이 과정을 공부하는 것이 목표라서 따로 데이터를 train : validation 으로 나누어 진행을 하지 않았기 때문에 Overfitting의 발생여부는 알아내기 힘들다.
<br><br>
 + 인퍼런스<br><br>
![result](https://user-images.githubusercontent.com/86700191/166405697-1bee4e1a-becb-497b-846b-41cf5c133ff8.PNG)
 

##  - 유의점
 + Korpora의 챗봇데이터 다운로드 문제<br><br>
    ![korpora_error](https://user-images.githubusercontent.com/86700191/165803432-fdb1e60f-2108-47cc-97bd-2208b3ac334d.PNG)

    ![err_reason](https://user-images.githubusercontent.com/86700191/165803441-3c78cfbe-d1e7-452d-a4f1-91fb460c0c8b.PNG)
    <br>
    korpora는 한국어로 되어 있는 오픈소스 말뭉치들의 다운로드와 전처리 기능을 제공하는 파이썬 라이브러리이다. 그런데 챗봇데이터에 대해서는 다운로드가 안되는 문제가 있는데
    이는 코드를 살펴보면 챗봇데이터를 다운받는 URL의 주소가 잘못 입력이 되어있어서 다운로드가 안된다. 정상적인 주소는 파일명인 `csv`앞에 있는 %20이 없어야 다운로드를 할 수 있다.<br><br>
 + CUDA ERROR<br><br>
![Cuda_memory_error](https://user-images.githubusercontent.com/86700191/166225313-44cbcef2-1b35-44c7-9524-f395b6583b46.PNG)
<br>
GPU의 메모리 부족 현상이다. 해당 에러는 미니 배치 하나의 평균 손실 값을 구하려고 하였을때, 실수로 `loss.item()`으로 스칼라 값만을 가져오지 않고 그라디언트를 계산한 함수에
대한 정보까지 한번에 더해서 생겼다. 하지만 근본적인 해결 방법으로는 batch_size 줄이기, CUDA 캐시 삭제(`torch.cuda.empty.cache()`) 가 있으며, 해당 코드는 캐시를 매 미니 배치마다 지우게 되어있다.


## - 사용한 언어 모델, 데이터
- [KoGPT2](https://github.com/SKT-AI/KoGPT2) : 사전 학습 모델
- [챗봇데이터](https://github.com/songys/Chatbot_data) : 파인튜닝 데이터
