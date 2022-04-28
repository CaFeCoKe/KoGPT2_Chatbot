# KoGPT2_Chatbot

## - 알고리즘 순서도<br><br>


## - GPT(Generative Pre-trained Transformer) 구성<br><br>


## - 결과

##  - 유의점
 + Korpora의 챗봇데이터 다운로드 문제<br><br>
    ![korpora_error](https://user-images.githubusercontent.com/86700191/165803432-fdb1e60f-2108-47cc-97bd-2208b3ac334d.PNG)

    ![err_reason](https://user-images.githubusercontent.com/86700191/165803441-3c78cfbe-d1e7-452d-a4f1-91fb460c0c8b.PNG)
    <br><br>
    korpora는 한국어로 되어 있는 오픈소스 말뭉치들의 다운로드와 전처리 기능을 제공하는 파이썬 라이브러리이다. 그런데 챗봇데이터에 대해서는 다운로드가 안되는 문제가 있는데
    이는 코드를 살펴보면 챗봇데이터를 다운받는 URL의 주소가 잘못 입력이 되어있어서 다운로드가 안된다. 정상적인 주소는 파일명인 `csv`앞에 있는 %20이 없어야 다운로드를 할 수 있다.
## - 사용한 언어 모델, 데이터
- [KoGPT2](https://github.com/SKT-AI/KoGPT2) : 사전 학습 모델

## - 참고 사이트


