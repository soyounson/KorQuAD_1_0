# 🐝 [KorQuAD 1.0](https://korquad.github.io/KorQuad%201.0/)

<img width="616" alt="Screen Shot 2022-05-27 at 00 14 16" src="https://user-images.githubusercontent.com/40614421/170518203-eeafc607-8093-492c-98dc-537f5c189b63.png">

**written by Soyoun Son**         
**Date : 053122**

### ☺︎ Purpose
- publicservant_AI(공무원 AI) [2]이 Bert 이용해서 KorQuAD1.0을 분석/예측 한것을 그대로 따라가면서 이해하는 작업을 수행한다.                        
- 모든 과정은 [2,2-1]에 기록되어 있다.                         
- 이 글은 처음으로 KorQUAD를 처음 접하는 입장에서 이해하고 배우는 것을 목표로 한다.                         

### ☺︎ KorQuAD란 [1]?
- The Korean Question Answering Dataset (KorQuAD)
- KorQuAD 1.0은 한국어 Machine Reading Comprehension을 위해 만든 데이터셋
- 모든 질의에 대한 답변은 해당 Wikipedia article 문단의 일부 하위 영역으로 이루어짐
- Stanford Question Answering Dataset(SQuAD) v1.0과 동일한 방식으로 구성됨

### ☺︎ Dataset [1]
KorQuAD 1.0의 전체 데이터는 1,560 개의 Wikipedia article에 대해 10,645 건의 문단과 66,181 개의 질의응답 쌍으로, **Training set 60,407 개**, **Dev set 5,774 개**의 질의응답쌍으로 구분함 

### ☺︎ 일반적인 Data Analysis processin of NLP 
- [x] ☺︎ Load Dataset 
- [ ] ☺︎ Data cleaning 
  - [ ] Capitalization/ Lower case
  - [ ] Expand the Contractions
  - [ ] Noise Removal
  - [ ] Remove punctuations
  - [ ] Other Manual Text Cleaning Tasks
   
- [x] ☺︎ Preprocessing              
  - [x] tokenization         
  - [ ] remove stop words         
  - [ ] stemming           
  - [ ] Part of Speech Tagging (POS tagging)
  - [ ] Lemmatization             
  - [ ] Other (Optional) Text Preprocessing Techniques 
          
- [ ] ☺︎ Feature extraction            
  - [ ] weighted words - BOW          
  - [ ] countvectorizer          
  - [ ] TF-IDF          

- [ ] ☺︎ Embedding          
  - [ ] word2vec -> gensim          
  - [ ] Glove          
  - [ ] FastText          

- [x] ☺︎ Model
  - [x] Bert
  - [ ] Etc
  
- [x] ☺︎ Evaluation 

-----------------------------------------------
## 🦜 Pre-requests
### ☺︎ Bert (Bidirectional Encoder Representations from Transformers) [2,3]
Bidirectional 은 양방향, Encoder은 입력값을 숫자의 형태로 바꾸는 모듈이라 Bert는 문맥을 양방향으로 이해해서 숫자의 형태로 바꿔주는 딥러닝 모델임

<img width="719" alt="Screen Shot 2022-05-31 at 16 01 31" src="https://user-images.githubusercontent.com/40614421/171112076-12d95f31-7e0a-41de-8301-52a4356d11dd.png">

- Bert's model architecture is based on the encoder of transformer 
- Transformer는 2017년 구글에서 공개한 인코딩/디코딩 구조를 지닌 딥러닝 모델 
- 여기서, Encoder는 양방향, Decoder는 왼쪽에서 오른쪽으로 처리하는 단방향 형태 
  - Encoder Attention : incorporate context from both direction 
  - Decoder Attention : incorporate context from only left side 

<img width="500" alt="Screen Shot 2022-05-31 at 16 13 03" src="https://user-images.githubusercontent.com/40614421/171114075-c46dd464-0ffc-4d31-991d-0db7f7ef5213.png">

<img width="349" alt="Screen Shot 2022-05-31 at 16 16 32" src="https://user-images.githubusercontent.com/40614421/171114695-54dff042-e2f7-4467-b91f-276e0c8f457a.png">

- 사람이 labeling할 필요가 없음. 단순히 랜덤하게 단어 가려주고, 가려진 단어를 학습하게 하면 됨
- 한문장 뿐만 아니라 두문장을 입력받아서 학습이 가능함 (ex. Q&A : 따라서 우리가 KorQuAD에서 Bert를 사용할 수 있음) 
토큰끼리의 상관관계 뿐만 아니라 문장간의 상관관계도 학습이 가능함
- CLS ( a special token for classification) : 분류 테스크에 사용하기 위한 토큰으로 문장 전체가 하나의 벡터로 표현된 special token임
- SEP ( a special token for separate two sentence is one input) : 두 문장을 구분하기 위한 토큰 
- 
<img width="780" alt="Screen Shot 2022-05-31 at 17 02 01" src="https://user-images.githubusercontent.com/40614421/171123437-349954be-0684-4dea-b134-ec3460739b4a.png">

- Bert는 WordPiece Embedding사용해서 문장을 토큰 단위로 분류. 단순히 띄어쓰기로 토큰 분류하는 것 보다 효과적으로 분류함
- 세그멘트 임베딩 : 두 문장 중 각각의 문장에 서로 다른 숫자를 더해주는 것으로 딥러닝에게 두개의 다른 문장이 있다는 것을 알려주는 목적 
- 포지셔널 임베딩 : 토큰의 위치 알려줌, sin+cos function 사용 (phase and values (-1~1)) 절대적 위치가 아닌 상대적 위치 이용

<img width="932" alt="Screen Shot 2022-05-31 at 17 02 49" src="https://user-images.githubusercontent.com/40614421/171123586-9c1a3649-38e8-49f8-952e-1b74acc4fa88.png">

  - outputs different value for each position : 입력값에 따라 출력값의 위치가 달라짐 
  - each position has patterned increasing and decreasing : 딥러닝 모델이 이 증/감을 통해서 입력값의 상대적 위치 파락
  - no limit on input, no worry for longer sentences : 무한대 길이의 입력값도 상대적 위치를 출력이 가능함 (-1 <= output <= 1)

#### ☻ Difference between traditional Language Model (LM) and Bert 
Bert는 양방향 학습
<img width="779" alt="Screen Shot 2022-05-31 at 16 18 36" src="https://user-images.githubusercontent.com/40614421/171115100-13fdd476-39c0-4d4c-8860-02262fbda5be.png">

- 단방향 LM : 현재까지 읽은 단어를 통해 다음 단어 예측 (ex. GPT)
- 양방향 LM : 동일한 문장을 그대로 학습하되, 가려진 단어 (masked token) 를 예측하도록 학습 (ex. BERT)

<img width="704" alt="Screen Shot 2022-05-31 at 17 07 14" src="https://user-images.githubusercontent.com/40614421/171124387-cf7bb926-4453-4283-b8b9-02ef6826d179.png">

GPT는 한번 학습시키는데 어마한 시간과 돈이 소요되는 반면 Bert는 상대적으로 시간과 돈이 소요. 하지만, Fine tuning을 개발자가 해줘야 하며 따로 시간과 돈이 소요됨
#### ☻ 4 different fine tuning of Bert 

![fine-tuning-BERT-in-different-tasks-Devlin-et-al-2019](https://user-images.githubusercontent.com/40614421/171124902-a029a26c-aeda-4136-8fa1-167b27435e50.png)

### ☺︎ SQUAD [3,3-1]
- SQUAD는 ANSWER를 다 예측하는 것이 아니고,  ANSWER 중에서도 시작단어와 끝 단어만을 예측함
- 시작과 끝을 알면 자연스럽게 가운데 위치한 글자들도 예측이 되는 것이므로 BERT 알고리즘을 사용함
- 우리가 풀고자 하는 KorQuAD와 동일함 

#### ☻ results

<img width="693" alt="Screen Shot 2022-05-31 at 16 51 38" src="https://user-images.githubusercontent.com/40614421/171121387-89b12cd1-43cd-40c1-8b4d-8398554f16a2.png">


-----------------------------------------------
## 🦦 케라스로 KorQuAD 구현하기 [2]
publicservant_AI(공무원 AI)에서 구현한 Keras, BERT이용해서 KorQuAD를 구현해보고 이해하는 작업 

> 이번 튜토리얼에서는 케라스와 BERT를 활용하여 KorQuAD를 구현해보고자 합니다. 이전에 배웠던 SQuAD와의 차이점은 단지 파일이 다르다는 점과, Tokenize를 정의할 때 네이버 한국어 영화 감성분석 할때처럼 새로운 Tokenize를 정의해서 한다는 점 말고는 SQuAD 랑 완전히 동일함

### ☺︎ Dataset
<img width="1176" alt="Screen Shot 2022-05-31 at 11 38 14" src="https://user-images.githubusercontent.com/40614421/171081910-45970881-d5da-4df9-aa4d-c426bdc3f132.png">

answer_start : 정답이 몇번째에서 시작하는지 나타냄 

### ☺︎ Bert 사전 설정 
<img width="1164" alt="Screen Shot 2022-05-31 at 11 40 59" src="https://user-images.githubusercontent.com/40614421/171082189-5e2ccce0-3fd4-4d76-9a11-e4c8ff346cc2.png">

- Bert 훈련을 위한 사전 설정을 함 
- SEQ_LEN : 문장의 최대 길이 (Bert input으로 들어갈 문장의 길이, 즉 Question + context의 길이를 의미함)
- SEQ_LEN 보다 문장의 길이가 작다면 남은 부분은 0이 채워지고, 만약에 SEQ_LEN보다 문장 길이가 길다면 SEQ_LEN을 초과하는 부분이 잘리게 됨 (본 문제에서는 메모리 문제 등으로 384로 정함)                                                          
- BATCH_SIZE는 메모리 초과 같은 문제를 방지하기 위해 작은 수인 10으로 정했습니다. 그리고 총 훈련 에포크 수는 1로 정함
- 학습율(LR;Learning rate)은 3e-5로 작게 정함                                                               
- pretrained_path는 bert 사전학습 모형이 있는 폴더를 의미함                     
- 그리고 우리가 분석할 문장이 들어있는 칼럼의 제목인 document와 긍정인지 부정인지 알려주는 칼럼을 label로 정해줌               

### ☺︎ Preprocessing : Tokenizer

<img width="1169" alt="Screen Shot 2022-05-31 at 11 43 24" src="https://user-images.githubusercontent.com/40614421/171082440-91616fe8-fb3f-4764-9b01-15bf5d87d5e4.png">

- vocab.txt에 있는 단어에 인덱스를 추가해주는 token_dict라는 딕셔너리를 생성함                                                                           
- 우리가 분석할 문장이 토큰화가 되고, 그 다음에는 인덱스(숫자)로 변경되어서 버트 신경망에 인풋으로 들어게 됨                                                                    
<img width="1167" alt="Screen Shot 2022-05-31 at 11 44 16" src="https://user-images.githubusercontent.com/40614421/171082548-8fc9c6f5-76f7-48ba-a1d1-b5061fc4294a.png">

- BERT의 토큰화는 단어를 분리하는 토큰화 방식입니다. wordpiece(단어조각?) 방식이라고 하는데, 이는 한국어를 형태소로 꼭 변환해야 할 문제를 해결해주며, 의미가 있는 단어는 밀접하게 연관이 되게 하는 장점까지 갖추고 있음
                                               
- 단어의 첫 시작은 ##가 붙지 않지만, 단어에 포함되면서 단어의 시작이 아닌 부분에는 ##가 붙는 것이 특징임                                                
- 네이버 감성분석에서 했던 것처럼, 한국어 감성분석에서는 새로 토크나이저 클래스를 상속을 받아서, 토크나이저를 재정의 해주어야함 (그렇지 않으면 완전자모분리 현상 발생)(완전자모분리 : 자음과 모음이 분리되는 현상)                

#### ☻ 토큰화 확인 
<img width="1158" alt="Screen Shot 2022-05-31 at 11 46 46" src="https://user-images.githubusercontent.com/40614421/171082814-3893dcb1-77f1-45be-8775-ba422d9911eb.png">

- 토큰화가 잘 되었는지 확인해 봅니다. 버트 모형은 문장 앞에 꼭 [CLS]라는 문자가 위치하고, [SEP]라는 문자가 끝에 위치함                 ([CLS]는 문장의 시작으로 Bert input의 맨 앞에 위치해야함, [SEP]는 문장의 끝을 의미하고 문장의 끝에 항상 위치)             
- 위에서 언급했던 단어의 시작이 아닌 부분에 ##가 붙음 (예, '##어', '##큰', '##화', '##되', '##니')                                 
#### 🔍 버트모형의 input 
<img width="1092" alt="Screen Shot 2022-05-31 at 11 51 50" src="https://user-images.githubusercontent.com/40614421/171083307-67a1d2ab-a754-4c28-9623-66eca5c26d04.png">

- 버트 모형에 들어갈 인풋은 토큰, 세그먼트, 포지션으로 구성
- 버트에 인풋으로 들어가는 토큰은 문장을 토크나이징 한 후, 인덱스 번호를 매긴 것 
- 세그먼트는 예를 들어 문장이 두 개가 있다면, 앞의 문장과 뒤의 문장을 구분하는 것, 위치를 알려줌  
- 포지션 임베딩은 단순히 단어의 위치를 말함
- 토큰, 세그먼트, 포지션을 인풋으로 버트 모형에 넣으면 기하학적인 문장 공간으로 임베딩이 됨
- 그림을 보면 my dog is cute, he likes play ##ing 두 문장이 있는데, KorQUAD 문제에서는 첫번째 문장이 질문, 두번째 문장이 context가 되고, 이 두 문장이 합쳐져서 하나의 문장으로 들어가게 됨

#### ☻ KorQuAD데이터의 토큰화 
우리가 로드하였던 KorQUAD 데이터를 버트 모형의 입력에 맞게 변형해주는 함수를 정의

<img width="1164" alt="Screen Shot 2022-05-31 at 11 55 49" src="https://user-images.githubusercontent.com/40614421/171083743-1444193b-3750-4d9d-b0f0-15969354f3d5.png">

- 함수 내부에 tokenizer.encode 함수가 버트 모형을 토큰화해주고 토큰화 된 단어를 인덱스에 맞게 숫자로 바꿔주게 됨
- [CLS] 질문 [SEP] 문장 [SEP] 이런 방식으로 질문과 문장이 인풋으로 들어가게 됩니다. SEQ_LEN이 384로 지정되어 있어서 길이가 384가 넘는 인풋은 문장 부분이 잘려서 들어가게 됨


<img width="1167" alt="Screen Shot 2022-05-31 at 12 06 52" src="https://user-images.githubusercontent.com/40614421/171084881-95588891-4894-46dc-af28-202efa3e7b87.png">

- 우리의 목표는, 질문(question)과 문장(context)를 받아서, 정답(text)를 맞추는 모델을 만드는 것
- 정답을 통째로 맞추는 것이 아니라, 토큰화된 것의 맨 앞 단어와, 맨 뒷 단어임 
- 토큰화된 정답은 ['[CLS]', 'saint', 'bern', '##ade', '##tte', 'sou', '##bir', '##ous', '[SEP]'] 인데, 여기서 saint에 해당하는 위치와 ##ous에 해당하는 위치를 맞추는 버트 모형을 파인튜닝 하려 하는 것

그래서 밑에 convert_data 함수에서, 정답(text) 길이만큼 문장(context)를 슬라이딩 하면서 만약에 문장이 정답을 포함하는 위치에 도달하면, 문장에서 정답의 맨 앞이 우리가 예측할 1번째 정답, 정답의 맨 뒤가 우리가 예측할 2번째 정답이 되게 됩니다.

### ☺︎ Train the model 
#### ☻ Input 
- 총 2개
- 첫번째 인풋은 토큰화 된 것이 인덱싱되어 숫자로 변환된 것
- 두번째 인풋은 앞문장인지 뒷문장인지 알려주는 숫자 
- 포지션 : 단어 순서에 따라서 자동으로 부여됩니다.

#### ☻ Model architecture [2]
Training을 False로 두어서 Bert 모델에서, 마지막 트랜스포머 계층까지만 모델이 로드되게 함 (12층의 트랜스포머 계층)

<img width="1167" alt="Screen Shot 2022-05-31 at 12 09 25" src="https://user-images.githubusercontent.com/40614421/171085135-8d6e4a28-a3f5-4354-b867-a7c89c04f324.png">

#### ☻ Call Bert 
<img width="1162" alt="Screen Shot 2022-05-31 at 12 19 34" src="https://user-images.githubusercontent.com/40614421/171086132-b803bbbe-b0ba-42b1-bbaa-04287634ca13.png">

BERT 모델을 출력하는 함수를 지정하고, start_answer, end_answer를 예측

<img width="1168" alt="Screen Shot 2022-05-31 at 12 24 07" src="https://user-images.githubusercontent.com/40614421/171086581-83bd7f74-71ac-483a-88ac-721b4b47a455.png">

버트 모형을 다시 훈련시키는데, 이번에는 validation_split을 입력하지 않아서 전체 데이터가 훈련 되도록 만들어 줌

<img width="1159" alt="Screen Shot 2022-05-31 at 12 25 09" src="https://user-images.githubusercontent.com/40614421/171086695-6b89fb72-847b-4c79-b650-b0b66fec02e8.png">

### ☺︎ Predict w/ test datasets
- KorQUAD 데이터 셋에서 test 용도로 쓰이는 dev 파일을 PANDAS DATAFRAME 형식으로 불러오는 함수를 정의함
- Test의 경우, train 데이터와 모양이 약간 다르기 때문에 함수를 새롭게 정의
- 
#### ☻ Test data
테스트 데이터확인 

<img width="1160" alt="Screen Shot 2022-05-31 at 12 26 50" src="https://user-images.githubusercontent.com/40614421/171086854-4ecb41c9-1b1a-45fb-9358-fd074705eee1.png">

#### ☻ Prediction 
<img width="1173" alt="Screen Shot 2022-05-31 at 12 30 33" src="https://user-images.githubusercontent.com/40614421/171087202-c90f549e-c1f3-44b8-9601-4b586c00ce4e.png">

<img width="1110" alt="Screen Shot 2022-05-31 at 12 31 00" src="https://user-images.githubusercontent.com/40614421/171087248-88ad242f-1fa9-48f0-9ac9-d42528d3686a.png">

### ☺︎ 결과 확인 

<img width="1168" alt="Screen Shot 2022-05-31 at 12 28 24" src="https://user-images.githubusercontent.com/40614421/171086973-5169e4b4-d0ce-44d3-8054-d64a313a39c0.png">

### ☺︎ Reference
- [1] [KorQuAD](https://korquad.github.io/KorQuad%201.0/)
- [2] [publicservant_AI(공무원 AI)](https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
- [2-1] [Colab:publicservant_AI(공무원 AI)](https://colab.research.google.com/github/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
- [3] [딥러닝 자연어처리 : BERT 이해하기](https://www.youtube.com/watch?v=30SvdoA6ApE)
- [4] [BERT로 Q&A 구현해보기 With SQuAD AND KERAS](https://www.youtube.com/watch?v=LuApA264Wbs)
- [4-1] [케라스로 Q&A 구현하기 w/ SQUAD](https://github.com/kimwoonggon/publicservant_AI/blob/master/(Uncased_Squad_V1_1)_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_Q%26A_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
