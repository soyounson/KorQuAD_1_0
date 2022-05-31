# 🐝 (KorQuAD 1.0)[https://korquad.github.io/KorQuad%201.0/]

<img width="616" alt="Screen Shot 2022-05-27 at 00 14 16" src="https://user-images.githubusercontent.com/40614421/170518203-eeafc607-8093-492c-98dc-537f5c189b63.png">

**written by Soyoun Son**         
**Date : 053122**

### ☺︎ KorQuAD란 [1]?
The Korean Question Answering Dataset (KorQuAD)

KorQuAD 1.0은 한국어 Machine Reading Comprehension을 위해 만든 데이터셋입니다. 모든 질의에 대한 답변은 해당 Wikipedia article 문단의 일부 하위 영역으로 이루어집니다. Stanford Question Answering Dataset(SQuAD) v1.0과 동일한 방식으로 구성되었습니다.


### ☺︎ Dataset [1]
KorQuAD 1.0의 전체 데이터는 1,560 개의 Wikipedia article에 대해 10,645 건의 문단과 66,181 개의 질의응답 쌍으로, **Training set 60,407 개**, **Dev set 5,774 개**의 질의응답쌍으로 구분하였습니다.

### ☺︎ ref : 케라스로 KorQuAD 구현하기
publicservant_AI(공무원 AI)[2] 에서 구현한 Keras, BERT이용해서 KorQuAD를 구현해보고 이해하는 작업 

> 이번 튜토리얼에서는 케라스와 BERT를 활용하여 KorQuAD를 구현해보고자 합니다. 이전에 배웠던 SQuAD와의 차이점은 단지 파일이 다르다는 점과, Tokenize를 정의할 때 네이버 한국어 영화 감성분석 할때처럼 새로운 Tokenize를 정의해서 한다는 점 말고는 SQuAD 랑 완전히 동일합니다.

### ☺︎ Data Analysis processin of NLP 
- [ ] ☺︎ Data cleaning 
  - Capitalization/ Lower case
  - Expand the Contractions
  - Noise Removal
  - Remove punctuations
  - Other Manual Text Cleaning Tasks
   
- [ ] ☺︎ Preprocessing              
  - tokenization         
  - remove stop words         
  - stemming           
  - Part of Speech Tagging (POS tagging)
  - Lemmatization             
  - Other (Optional) Text Preprocessing Techniques 
          
- [ ] ☺︎ Feature extraction            
  - weighted words - BOW          
  - countvectorizer          
  - TF-IDF          

- [ ] ☺︎ Embedding          
  - word2vec -> gensim          
  - Glove          
  - FastText          

- [ ] ☺︎ Model
          
- [ ] ☺︎ Evaluation 



#### ☻ Train dataset : train.csv 


ref
[1] (KorQuAD)[https://korquad.github.io/KorQuad%201.0/]
[2] (publicservant_AI(공무원 AI))[https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb]


Slides : https://www.slideshare.net/SeungyoungLim/korquad-introduction
### ref : https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb

### ref: https://colab.research.google.com/github/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb


https://github.com/monologg/KoBERT-KorQuAD
https://github.com/y-rok/BERT-KorQuAD-dynamic-training
https://github.com/lyeoni/KorQuAD
https://github.sre.pub/kizoey/mrc-kobert-rtt
