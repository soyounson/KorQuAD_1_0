# 🐝 [KorQuAD 1.0](https://korquad.github.io/KorQuad%201.0/)

<img width="616" alt="Screen Shot 2022-05-27 at 00 14 16" src="https://user-images.githubusercontent.com/40614421/170518203-eeafc607-8093-492c-98dc-537f5c189b63.png">

**written by Soyoun Son**         
**Date : 053122**

### ☺︎ KorQuAD란 [1]?
The Korean Question Answering Dataset (KorQuAD)

KorQuAD 1.0은 한국어 Machine Reading Comprehension을 위해 만든 데이터셋입니다. 모든 질의에 대한 답변은 해당 Wikipedia article 문단의 일부 하위 영역으로 이루어집니다. Stanford Question Answering Dataset(SQuAD) v1.0과 동일한 방식으로 구성되었습니다.

### ☺︎ Dataset [1]
KorQuAD 1.0의 전체 데이터는 1,560 개의 Wikipedia article에 대해 10,645 건의 문단과 66,181 개의 질의응답 쌍으로, **Training set 60,407 개**, **Dev set 5,774 개**의 질의응답쌍으로 구분하였습니다.

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
  - [ ] Deep learning based models
  - [x] Bert
  - [ ] Etc
  
- [ ] ☺︎ Evaluation 

-----------------------------------------------
## 케라스로 KorQuAD 구현하기 [2]
publicservant_AI(공무원 AI)에서 구현한 Keras, BERT이용해서 KorQuAD를 구현해보고 이해하는 작업 

> 이번 튜토리얼에서는 케라스와 BERT를 활용하여 KorQuAD를 구현해보고자 합니다. 이전에 배웠던 SQuAD와의 차이점은 단지 파일이 다르다는 점과, Tokenize를 정의할 때 네이버 한국어 영화 감성분석 할때처럼 새로운 Tokenize를 정의해서 한다는 점 말고는 SQuAD 랑 완전히 동일합니다.

### ☺︎ Dataset
<img width="1176" alt="Screen Shot 2022-05-31 at 11 38 14" src="https://user-images.githubusercontent.com/40614421/171081910-45970881-d5da-4df9-aa4d-c426bdc3f132.png">

### ☺︎ Bert 사전 설정 
<img width="1164" alt="Screen Shot 2022-05-31 at 11 40 59" src="https://user-images.githubusercontent.com/40614421/171082189-5e2ccce0-3fd4-4d76-9a11-e4c8ff346cc2.png">

- bert 훈련을 위한 사전 설정을 합니다. SEQ_LEN은 문장의 최대 길이입니다. SEQ_LEN 보다 문장의 길이가 작다면 남은 부분은 0이 채워지고, 만약에 SEQ_LEN보다 문장 길이가 길다면 SEQ_LEN을 초과하는 부분이 잘리게 됩니다. (본 문제에서는 메모리 문제 등으로 384로 정했습니다.)
- BATCH_SIZE는 메모리 초과 같은 문제를 방지하기 위해 작은 수인 10으로 정했습니다. 그리고 총 훈련 에포크 수는 1로 정했습니다. 학습율(LR;Learning rate)은 3e-5로 작게 정했습니다.
- pretrained_path는 bert 사전학습 모형이 있는 폴더를 의미합니다.
- 그리고 우리가 분석할 문장이 들어있는 칼럼의 제목인 document와 긍정인지 부정인지 알려주는 칼럼을 label로 정해줍니다

### ☺︎ Preprocessing : Tokenizer

<img width="1169" alt="Screen Shot 2022-05-31 at 11 43 24" src="https://user-images.githubusercontent.com/40614421/171082440-91616fe8-fb3f-4764-9b01-15bf5d87d5e4.png">
- vocab.txt에 있는 단어에 인덱스를 추가해주는 token_dict라는 딕셔너리를 생성합니다.
- 우리가 분석할 문장이 토큰화가 되고, 그 다음에는 인덱스(숫자)로 변경되어서 버트 신경망에 인풋으로 들어게 됩니다.

<img width="1167" alt="Screen Shot 2022-05-31 at 11 44 16" src="https://user-images.githubusercontent.com/40614421/171082548-8fc9c6f5-76f7-48ba-a1d1-b5061fc4294a.png">
- BERT의 토큰화는 단어를 분리하는 토큰화 방식입니다. wordpiece(단어조각?) 방식이라고 하는데, 이는 한국어를 형태소로 꼭 변환해야 할 문제를 해결해주며, 의미가 있는 단어는 밀접하게 연관이 되게 하는 장점까지 갖추고 있습니다.
- 단어의 첫 시작은 ##가 붙지 않지만, 단어에 포함되면서 단어의 시작이 아닌 부분에는 ##가 붙는 것이 특징입니다.
- 네이버 감성분석에서 했던 것처럼, 한국어 감성분석에서는 새로 토크나이저 클래스를 상속을 받아서, 토크나이저를 재정의 해주어야 합니다.(그렇지 않으면 완전자모분리 현상 발생)
(완전자모분리 : 자음과 모음이 분리되는 현상)

#### ☻ 토큰화 확인 
<img width="1158" alt="Screen Shot 2022-05-31 at 11 46 46" src="https://user-images.githubusercontent.com/40614421/171082814-3893dcb1-77f1-45be-8775-ba422d9911eb.png">
토큰화가 잘 되었는지 확인해 봅니다. 버트 모형은 문장 앞에 꼭 [CLS]라는 문자가 위치하고, [SEP]라는 문자가 끝에 위치합니다.
[CLS]는 문장의 시작, [SEP]는 문장의 끝을 의미합니다.

















### ☺︎ Reference
[1] [KorQuAD](https://korquad.github.io/KorQuad%201.0/)

[2] [publicservant_AI(공무원 AI)](https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)


Slides : https://www.slideshare.net/SeungyoungLim/korquad-introduction
### ref : https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb

### ref: https://colab.research.google.com/github/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb


https://github.com/monologg/KoBERT-KorQuAD
https://github.com/y-rok/BERT-KorQuAD-dynamic-training
https://github.com/lyeoni/KorQuAD
https://github.sre.pub/kizoey/mrc-kobert-rtt
