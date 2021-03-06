# ๐ [KorQuAD 1.0](https://korquad.github.io/KorQuad%201.0/)

<img width="616" alt="Screen Shot 2022-05-27 at 00 14 16" src="https://user-images.githubusercontent.com/40614421/170518203-eeafc607-8093-492c-98dc-537f5c189b63.png">

**written by Soyoun Son**         
**Date : 053122**

### โบ๏ธ Purpose
- publicservant_AI(๊ณต๋ฌด์ AI) [2]์ด Bert ์ด์ฉํด์ KorQuAD1.0์ ๋ถ์/์์ธก ํ๊ฒ์ ๊ทธ๋๋ก ๋ฐ๋ผ๊ฐ๋ฉด์ ์ดํดํ๋ ์์์ ์ํํ๋ค.                        
- ๋ชจ๋  ๊ณผ์ ์ [2,2-1]์ ๊ธฐ๋ก๋์ด ์๋ค.                         
- ์ด ๊ธ์ ์ฒ์์ผ๋ก KorQUAD๋ฅผ ์ฒ์ ์ ํ๋ ์์ฅ์์ ์ดํดํ๊ณ  ๋ฐฐ์ฐ๋ ๊ฒ์ ๋ชฉํ๋ก ํ๋ค.                         

### โบ๏ธ KorQuAD๋ [1]?
- The Korean Question Answering Dataset (KorQuAD)
- KorQuAD 1.0์ ํ๊ตญ์ด Machine Reading Comprehension์ ์ํด ๋ง๋  ๋ฐ์ดํฐ์
- ๋ชจ๋  ์ง์์ ๋ํ ๋ต๋ณ์ ํด๋น Wikipedia article ๋ฌธ๋จ์ ์ผ๋ถ ํ์ ์์ญ์ผ๋ก ์ด๋ฃจ์ด์ง
- Stanford Question Answering Dataset(SQuAD) v1.0๊ณผ ๋์ผํ ๋ฐฉ์์ผ๋ก ๊ตฌ์ฑ๋จ

### โบ๏ธ Dataset [1]
KorQuAD 1.0์ ์ ์ฒด ๋ฐ์ดํฐ๋ 1,560 ๊ฐ์ Wikipedia article์ ๋ํด 10,645 ๊ฑด์ ๋ฌธ๋จ๊ณผ 66,181 ๊ฐ์ ์ง์์๋ต ์์ผ๋ก, **Training set 60,407 ๊ฐ**, **Dev set 5,774 ๊ฐ**์ ์ง์์๋ต์์ผ๋ก ๊ตฌ๋ถํจ 

### โบ๏ธ ์ผ๋ฐ์ ์ธ Data Analysis processin of NLP 
- [x] โบ๏ธ Load Dataset 
- [ ] โบ๏ธ Data cleaning 
  - [ ] Capitalization/ Lower case
  - [ ] Expand the Contractions
  - [ ] Noise Removal
  - [ ] Remove punctuations
  - [ ] Other Manual Text Cleaning Tasks
   
- [x] โบ๏ธ Preprocessing              
  - [x] tokenization         
  - [ ] remove stop words         
  - [ ] stemming           
  - [ ] Part of Speech Tagging (POS tagging)
  - [ ] Lemmatization             
  - [ ] Other (Optional) Text Preprocessing Techniques 
          
- [ ] โบ๏ธ Feature extraction            
  - [ ] weighted words - BOW          
  - [ ] countvectorizer          
  - [ ] TF-IDF          

- [ ] โบ๏ธ Embedding          
  - [ ] word2vec -> gensim          
  - [ ] Glove          
  - [ ] FastText          

- [x] โบ๏ธ Model
  - [x] Bert
  - [ ] Etc
  
- [x] โบ๏ธ Evaluation 

-----------------------------------------------
## ๐ฆ Pre-requests
### โบ๏ธ Bert (Bidirectional Encoder Representations from Transformers) [2,3]
Bidirectional ์ ์๋ฐฉํฅ, Encoder์ ์๋ ฅ๊ฐ์ ์ซ์์ ํํ๋ก ๋ฐ๊พธ๋ ๋ชจ๋์ด๋ผ Bert๋ ๋ฌธ๋งฅ์ ์๋ฐฉํฅ์ผ๋ก ์ดํดํด์ ์ซ์์ ํํ๋ก ๋ฐ๊ฟ์ฃผ๋ ๋ฅ๋ฌ๋ ๋ชจ๋ธ์

<img width="719" alt="Screen Shot 2022-05-31 at 16 01 31" src="https://user-images.githubusercontent.com/40614421/171112076-12d95f31-7e0a-41de-8301-52a4356d11dd.png">

- Bert's model architecture is based on the encoder of transformer 
- Transformer๋ 2017๋ ๊ตฌ๊ธ์์ ๊ณต๊ฐํ ์ธ์ฝ๋ฉ/๋์ฝ๋ฉ ๊ตฌ์กฐ๋ฅผ ์ง๋ ๋ฅ๋ฌ๋ ๋ชจ๋ธ 
- ์ฌ๊ธฐ์, Encoder๋ ์๋ฐฉํฅ, Decoder๋ ์ผ์ชฝ์์ ์ค๋ฅธ์ชฝ์ผ๋ก ์ฒ๋ฆฌํ๋ ๋จ๋ฐฉํฅ ํํ 
  - Encoder Attention : incorporate context from both direction 
  - Decoder Attention : incorporate context from only left side 

<img width="500" alt="Screen Shot 2022-05-31 at 16 13 03" src="https://user-images.githubusercontent.com/40614421/171114075-c46dd464-0ffc-4d31-991d-0db7f7ef5213.png">

<img width="349" alt="Screen Shot 2022-05-31 at 16 16 32" src="https://user-images.githubusercontent.com/40614421/171114695-54dff042-e2f7-4467-b91f-276e0c8f457a.png">

- ์ฌ๋์ด labelingํ  ํ์๊ฐ ์์. ๋จ์ํ ๋๋คํ๊ฒ ๋จ์ด ๊ฐ๋ ค์ฃผ๊ณ , ๊ฐ๋ ค์ง ๋จ์ด๋ฅผ ํ์ตํ๊ฒ ํ๋ฉด ๋จ
- ํ๋ฌธ์ฅ ๋ฟ๋ง ์๋๋ผ ๋๋ฌธ์ฅ์ ์๋ ฅ๋ฐ์์ ํ์ต์ด ๊ฐ๋ฅํจ (ex. Q&A : ๋ฐ๋ผ์ ์ฐ๋ฆฌ๊ฐ KorQuAD์์ Bert๋ฅผ ์ฌ์ฉํ  ์ ์์) 
ํ ํฐ๋ผ๋ฆฌ์ ์๊ด๊ด๊ณ ๋ฟ๋ง ์๋๋ผ ๋ฌธ์ฅ๊ฐ์ ์๊ด๊ด๊ณ๋ ํ์ต์ด ๊ฐ๋ฅํจ
- CLS ( a special token for classification) : ๋ถ๋ฅ ํ์คํฌ์ ์ฌ์ฉํ๊ธฐ ์ํ ํ ํฐ์ผ๋ก ๋ฌธ์ฅ ์ ์ฒด๊ฐ ํ๋์ ๋ฒกํฐ๋ก ํํ๋ special token์
- SEP ( a special token for separate two sentence is one input) : ๋ ๋ฌธ์ฅ์ ๊ตฌ๋ถํ๊ธฐ ์ํ ํ ํฐ 
- 
<img width="780" alt="Screen Shot 2022-05-31 at 17 02 01" src="https://user-images.githubusercontent.com/40614421/171123437-349954be-0684-4dea-b134-ec3460739b4a.png">

- Bert๋ WordPiece Embedding์ฌ์ฉํด์ ๋ฌธ์ฅ์ ํ ํฐ ๋จ์๋ก ๋ถ๋ฅ. ๋จ์ํ ๋์ด์ฐ๊ธฐ๋ก ํ ํฐ ๋ถ๋ฅํ๋ ๊ฒ ๋ณด๋ค ํจ๊ณผ์ ์ผ๋ก ๋ถ๋ฅํจ
- ์ธ๊ทธ๋ฉํธ ์๋ฒ ๋ฉ : ๋ ๋ฌธ์ฅ ์ค ๊ฐ๊ฐ์ ๋ฌธ์ฅ์ ์๋ก ๋ค๋ฅธ ์ซ์๋ฅผ ๋ํด์ฃผ๋ ๊ฒ์ผ๋ก ๋ฅ๋ฌ๋์๊ฒ ๋๊ฐ์ ๋ค๋ฅธ ๋ฌธ์ฅ์ด ์๋ค๋ ๊ฒ์ ์๋ ค์ฃผ๋ ๋ชฉ์  
- ํฌ์ง์๋ ์๋ฒ ๋ฉ : ํ ํฐ์ ์์น ์๋ ค์ค, sin+cos function ์ฌ์ฉ (phase and values (-1~1)) ์ ๋์  ์์น๊ฐ ์๋ ์๋์  ์์น ์ด์ฉ

<img width="932" alt="Screen Shot 2022-05-31 at 17 02 49" src="https://user-images.githubusercontent.com/40614421/171123586-9c1a3649-38e8-49f8-952e-1b74acc4fa88.png">

  - outputs different value for each position : ์๋ ฅ๊ฐ์ ๋ฐ๋ผ ์ถ๋ ฅ๊ฐ์ ์์น๊ฐ ๋ฌ๋ผ์ง 
  - each position has patterned increasing and decreasing : ๋ฅ๋ฌ๋ ๋ชจ๋ธ์ด ์ด ์ฆ/๊ฐ์ ํตํด์ ์๋ ฅ๊ฐ์ ์๋์  ์์น ํ๋ฝ
  - no limit on input, no worry for longer sentences : ๋ฌดํ๋ ๊ธธ์ด์ ์๋ ฅ๊ฐ๋ ์๋์  ์์น๋ฅผ ์ถ๋ ฅ์ด ๊ฐ๋ฅํจ (-1 <= output <= 1)

#### โป Difference between traditional Language Model (LM) and Bert 
Bert๋ ์๋ฐฉํฅ ํ์ต
<img width="779" alt="Screen Shot 2022-05-31 at 16 18 36" src="https://user-images.githubusercontent.com/40614421/171115100-13fdd476-39c0-4d4c-8860-02262fbda5be.png">

- ๋จ๋ฐฉํฅ LM : ํ์ฌ๊น์ง ์ฝ์ ๋จ์ด๋ฅผ ํตํด ๋ค์ ๋จ์ด ์์ธก (ex. GPT)
- ์๋ฐฉํฅ LM : ๋์ผํ ๋ฌธ์ฅ์ ๊ทธ๋๋ก ํ์ตํ๋, ๊ฐ๋ ค์ง ๋จ์ด (masked token) ๋ฅผ ์์ธกํ๋๋ก ํ์ต (ex. BERT)

<img width="704" alt="Screen Shot 2022-05-31 at 17 07 14" src="https://user-images.githubusercontent.com/40614421/171124387-cf7bb926-4453-4283-b8b9-02ef6826d179.png">

GPT๋ ํ๋ฒ ํ์ต์ํค๋๋ฐ ์ด๋งํ ์๊ฐ๊ณผ ๋์ด ์์๋๋ ๋ฐ๋ฉด Bert๋ ์๋์ ์ผ๋ก ์๊ฐ๊ณผ ๋์ด ์์. ํ์ง๋ง, Fine tuning์ ๊ฐ๋ฐ์๊ฐ ํด์ค์ผ ํ๋ฉฐ ๋ฐ๋ก ์๊ฐ๊ณผ ๋์ด ์์๋จ
#### โป 4 different fine tuning of Bert 

![fine-tuning-BERT-in-different-tasks-Devlin-et-al-2019](https://user-images.githubusercontent.com/40614421/171124902-a029a26c-aeda-4136-8fa1-167b27435e50.png)

### โบ๏ธ SQUAD [3,3-1]
- SQUAD๋ ANSWER๋ฅผ ๋ค ์์ธกํ๋ ๊ฒ์ด ์๋๊ณ ,  ANSWER ์ค์์๋ ์์๋จ์ด์ ๋ ๋จ์ด๋ง์ ์์ธกํจ
- ์์๊ณผ ๋์ ์๋ฉด ์์ฐ์ค๋ฝ๊ฒ ๊ฐ์ด๋ฐ ์์นํ ๊ธ์๋ค๋ ์์ธก์ด ๋๋ ๊ฒ์ด๋ฏ๋ก BERT ์๊ณ ๋ฆฌ์ฆ์ ์ฌ์ฉํจ
- ์ฐ๋ฆฌ๊ฐ ํ๊ณ ์ ํ๋ KorQuAD์ ๋์ผํจ 

#### โป results

<img width="693" alt="Screen Shot 2022-05-31 at 16 51 38" src="https://user-images.githubusercontent.com/40614421/171121387-89b12cd1-43cd-40c1-8b4d-8398554f16a2.png">


-----------------------------------------------
## ๐ฆฆ ์ผ๋ผ์ค๋ก KorQuAD ๊ตฌํํ๊ธฐ [2]
publicservant_AI(๊ณต๋ฌด์ AI)์์ ๊ตฌํํ Keras, BERT์ด์ฉํด์ KorQuAD๋ฅผ ๊ตฌํํด๋ณด๊ณ  ์ดํดํ๋ ์์ 

> ์ด๋ฒ ํํ ๋ฆฌ์ผ์์๋ ์ผ๋ผ์ค์ BERT๋ฅผ ํ์ฉํ์ฌ KorQuAD๋ฅผ ๊ตฌํํด๋ณด๊ณ ์ ํฉ๋๋ค. ์ด์ ์ ๋ฐฐ์ ๋ SQuAD์์ ์ฐจ์ด์ ์ ๋จ์ง ํ์ผ์ด ๋ค๋ฅด๋ค๋ ์ ๊ณผ, Tokenize๋ฅผ ์ ์ํ  ๋ ๋ค์ด๋ฒ ํ๊ตญ์ด ์ํ ๊ฐ์ฑ๋ถ์ ํ ๋์ฒ๋ผ ์๋ก์ด Tokenize๋ฅผ ์ ์ํด์ ํ๋ค๋ ์  ๋ง๊ณ ๋ SQuAD ๋ ์์ ํ ๋์ผํจ

### โบ๏ธ Dataset
<img width="1176" alt="Screen Shot 2022-05-31 at 11 38 14" src="https://user-images.githubusercontent.com/40614421/171081910-45970881-d5da-4df9-aa4d-c426bdc3f132.png">

answer_start : ์ ๋ต์ด ๋ช๋ฒ์งธ์์ ์์ํ๋์ง ๋ํ๋ 

### โบ๏ธ Bert ์ฌ์  ์ค์  
<img width="1164" alt="Screen Shot 2022-05-31 at 11 40 59" src="https://user-images.githubusercontent.com/40614421/171082189-5e2ccce0-3fd4-4d76-9a11-e4c8ff346cc2.png">

- Bert ํ๋ จ์ ์ํ ์ฌ์  ์ค์ ์ ํจ 
- SEQ_LEN : ๋ฌธ์ฅ์ ์ต๋ ๊ธธ์ด (Bert input์ผ๋ก ๋ค์ด๊ฐ ๋ฌธ์ฅ์ ๊ธธ์ด, ์ฆ Question + context์ ๊ธธ์ด๋ฅผ ์๋ฏธํจ)
- SEQ_LEN ๋ณด๋ค ๋ฌธ์ฅ์ ๊ธธ์ด๊ฐ ์๋ค๋ฉด ๋จ์ ๋ถ๋ถ์ 0์ด ์ฑ์์ง๊ณ , ๋ง์ฝ์ SEQ_LEN๋ณด๋ค ๋ฌธ์ฅ ๊ธธ์ด๊ฐ ๊ธธ๋ค๋ฉด SEQ_LEN์ ์ด๊ณผํ๋ ๋ถ๋ถ์ด ์๋ฆฌ๊ฒ ๋จ (๋ณธ ๋ฌธ์ ์์๋ ๋ฉ๋ชจ๋ฆฌ ๋ฌธ์  ๋ฑ์ผ๋ก 384๋ก ์ ํจ)                                                          
- BATCH_SIZE๋ ๋ฉ๋ชจ๋ฆฌ ์ด๊ณผ ๊ฐ์ ๋ฌธ์ ๋ฅผ ๋ฐฉ์งํ๊ธฐ ์ํด ์์ ์์ธ 10์ผ๋ก ์ ํ์ต๋๋ค. ๊ทธ๋ฆฌ๊ณ  ์ด ํ๋ จ ์ํฌํฌ ์๋ 1๋ก ์ ํจ
- ํ์ต์จ(LR;Learning rate)์ 3e-5๋ก ์๊ฒ ์ ํจ                                                               
- pretrained_path๋ bert ์ฌ์ ํ์ต ๋ชจํ์ด ์๋ ํด๋๋ฅผ ์๋ฏธํจ                     
- ๊ทธ๋ฆฌ๊ณ  ์ฐ๋ฆฌ๊ฐ ๋ถ์ํ  ๋ฌธ์ฅ์ด ๋ค์ด์๋ ์นผ๋ผ์ ์ ๋ชฉ์ธ document์ ๊ธ์ ์ธ์ง ๋ถ์ ์ธ์ง ์๋ ค์ฃผ๋ ์นผ๋ผ์ label๋ก ์ ํด์ค               

### โบ๏ธ Preprocessing : Tokenizer

<img width="1169" alt="Screen Shot 2022-05-31 at 11 43 24" src="https://user-images.githubusercontent.com/40614421/171082440-91616fe8-fb3f-4764-9b01-15bf5d87d5e4.png">

- vocab.txt์ ์๋ ๋จ์ด์ ์ธ๋ฑ์ค๋ฅผ ์ถ๊ฐํด์ฃผ๋ token_dict๋ผ๋ ๋์๋๋ฆฌ๋ฅผ ์์ฑํจ                                                                           
- ์ฐ๋ฆฌ๊ฐ ๋ถ์ํ  ๋ฌธ์ฅ์ด ํ ํฐํ๊ฐ ๋๊ณ , ๊ทธ ๋ค์์๋ ์ธ๋ฑ์ค(์ซ์)๋ก ๋ณ๊ฒฝ๋์ด์ ๋ฒํธ ์ ๊ฒฝ๋ง์ ์ธํ์ผ๋ก ๋ค์ด๊ฒ ๋จ                                                                    
<img width="1167" alt="Screen Shot 2022-05-31 at 11 44 16" src="https://user-images.githubusercontent.com/40614421/171082548-8fc9c6f5-76f7-48ba-a1d1-b5061fc4294a.png">

- BERT์ ํ ํฐํ๋ ๋จ์ด๋ฅผ ๋ถ๋ฆฌํ๋ ํ ํฐํ ๋ฐฉ์์๋๋ค. wordpiece(๋จ์ด์กฐ๊ฐ?) ๋ฐฉ์์ด๋ผ๊ณ  ํ๋๋ฐ, ์ด๋ ํ๊ตญ์ด๋ฅผ ํํ์๋ก ๊ผญ ๋ณํํด์ผ ํ  ๋ฌธ์ ๋ฅผ ํด๊ฒฐํด์ฃผ๋ฉฐ, ์๋ฏธ๊ฐ ์๋ ๋จ์ด๋ ๋ฐ์ ํ๊ฒ ์ฐ๊ด์ด ๋๊ฒ ํ๋ ์ฅ์ ๊น์ง ๊ฐ์ถ๊ณ  ์์
                                               
- ๋จ์ด์ ์ฒซ ์์์ ##๊ฐ ๋ถ์ง ์์ง๋ง, ๋จ์ด์ ํฌํจ๋๋ฉด์ ๋จ์ด์ ์์์ด ์๋ ๋ถ๋ถ์๋ ##๊ฐ ๋ถ๋ ๊ฒ์ด ํน์ง์                                                
- ๋ค์ด๋ฒ ๊ฐ์ฑ๋ถ์์์ ํ๋ ๊ฒ์ฒ๋ผ, ํ๊ตญ์ด ๊ฐ์ฑ๋ถ์์์๋ ์๋ก ํ ํฌ๋์ด์  ํด๋์ค๋ฅผ ์์์ ๋ฐ์์, ํ ํฌ๋์ด์ ๋ฅผ ์ฌ์ ์ ํด์ฃผ์ด์ผํจ (๊ทธ๋ ์ง ์์ผ๋ฉด ์์ ์๋ชจ๋ถ๋ฆฌ ํ์ ๋ฐ์)(์์ ์๋ชจ๋ถ๋ฆฌ : ์์๊ณผ ๋ชจ์์ด ๋ถ๋ฆฌ๋๋ ํ์)                

#### โป ํ ํฐํ ํ์ธ 
<img width="1158" alt="Screen Shot 2022-05-31 at 11 46 46" src="https://user-images.githubusercontent.com/40614421/171082814-3893dcb1-77f1-45be-8775-ba422d9911eb.png">

- ํ ํฐํ๊ฐ ์ ๋์๋์ง ํ์ธํด ๋ด๋๋ค. ๋ฒํธ ๋ชจํ์ ๋ฌธ์ฅ ์์ ๊ผญ [CLS]๋ผ๋ ๋ฌธ์๊ฐ ์์นํ๊ณ , [SEP]๋ผ๋ ๋ฌธ์๊ฐ ๋์ ์์นํจ                 ([CLS]๋ ๋ฌธ์ฅ์ ์์์ผ๋ก Bert input์ ๋งจ ์์ ์์นํด์ผํจ, [SEP]๋ ๋ฌธ์ฅ์ ๋์ ์๋ฏธํ๊ณ  ๋ฌธ์ฅ์ ๋์ ํญ์ ์์น)             
- ์์์ ์ธ๊ธํ๋ ๋จ์ด์ ์์์ด ์๋ ๋ถ๋ถ์ ##๊ฐ ๋ถ์ (์, '##์ด', '##ํฐ', '##ํ', '##๋', '##๋')                                 
#### ๐ ๋ฒํธ๋ชจํ์ input 
<img width="1092" alt="Screen Shot 2022-05-31 at 11 51 50" src="https://user-images.githubusercontent.com/40614421/171083307-67a1d2ab-a754-4c28-9623-66eca5c26d04.png">

- ๋ฒํธ ๋ชจํ์ ๋ค์ด๊ฐ ์ธํ์ ํ ํฐ, ์ธ๊ทธ๋จผํธ, ํฌ์ง์์ผ๋ก ๊ตฌ์ฑ
- ๋ฒํธ์ ์ธํ์ผ๋ก ๋ค์ด๊ฐ๋ ํ ํฐ์ ๋ฌธ์ฅ์ ํ ํฌ๋์ด์ง ํ ํ, ์ธ๋ฑ์ค ๋ฒํธ๋ฅผ ๋งค๊ธด ๊ฒ 
- ์ธ๊ทธ๋จผํธ๋ ์๋ฅผ ๋ค์ด ๋ฌธ์ฅ์ด ๋ ๊ฐ๊ฐ ์๋ค๋ฉด, ์์ ๋ฌธ์ฅ๊ณผ ๋ค์ ๋ฌธ์ฅ์ ๊ตฌ๋ถํ๋ ๊ฒ, ์์น๋ฅผ ์๋ ค์ค  
- ํฌ์ง์ ์๋ฒ ๋ฉ์ ๋จ์ํ ๋จ์ด์ ์์น๋ฅผ ๋งํจ
- ํ ํฐ, ์ธ๊ทธ๋จผํธ, ํฌ์ง์์ ์ธํ์ผ๋ก ๋ฒํธ ๋ชจํ์ ๋ฃ์ผ๋ฉด ๊ธฐํํ์ ์ธ ๋ฌธ์ฅ ๊ณต๊ฐ์ผ๋ก ์๋ฒ ๋ฉ์ด ๋จ
- ๊ทธ๋ฆผ์ ๋ณด๋ฉด my dog is cute, he likes play ##ing ๋ ๋ฌธ์ฅ์ด ์๋๋ฐ, KorQUAD ๋ฌธ์ ์์๋ ์ฒซ๋ฒ์งธ ๋ฌธ์ฅ์ด ์ง๋ฌธ, ๋๋ฒ์งธ ๋ฌธ์ฅ์ด context๊ฐ ๋๊ณ , ์ด ๋ ๋ฌธ์ฅ์ด ํฉ์ณ์ ธ์ ํ๋์ ๋ฌธ์ฅ์ผ๋ก ๋ค์ด๊ฐ๊ฒ ๋จ

#### โป KorQuAD๋ฐ์ดํฐ์ ํ ํฐํ 
์ฐ๋ฆฌ๊ฐ ๋ก๋ํ์๋ KorQUAD ๋ฐ์ดํฐ๋ฅผ ๋ฒํธ ๋ชจํ์ ์๋ ฅ์ ๋ง๊ฒ ๋ณํํด์ฃผ๋ ํจ์๋ฅผ ์ ์

<img width="1164" alt="Screen Shot 2022-05-31 at 11 55 49" src="https://user-images.githubusercontent.com/40614421/171083743-1444193b-3750-4d9d-b0f0-15969354f3d5.png">

- ํจ์ ๋ด๋ถ์ tokenizer.encode ํจ์๊ฐ ๋ฒํธ ๋ชจํ์ ํ ํฐํํด์ฃผ๊ณ  ํ ํฐํ ๋ ๋จ์ด๋ฅผ ์ธ๋ฑ์ค์ ๋ง๊ฒ ์ซ์๋ก ๋ฐ๊ฟ์ฃผ๊ฒ ๋จ
- [CLS] ์ง๋ฌธ [SEP] ๋ฌธ์ฅ [SEP] ์ด๋ฐ ๋ฐฉ์์ผ๋ก ์ง๋ฌธ๊ณผ ๋ฌธ์ฅ์ด ์ธํ์ผ๋ก ๋ค์ด๊ฐ๊ฒ ๋ฉ๋๋ค. SEQ_LEN์ด 384๋ก ์ง์ ๋์ด ์์ด์ ๊ธธ์ด๊ฐ 384๊ฐ ๋๋ ์ธํ์ ๋ฌธ์ฅ ๋ถ๋ถ์ด ์๋ ค์ ๋ค์ด๊ฐ๊ฒ ๋จ


<img width="1167" alt="Screen Shot 2022-05-31 at 12 06 52" src="https://user-images.githubusercontent.com/40614421/171084881-95588891-4894-46dc-af28-202efa3e7b87.png">

- ์ฐ๋ฆฌ์ ๋ชฉํ๋, ์ง๋ฌธ(question)๊ณผ ๋ฌธ์ฅ(context)๋ฅผ ๋ฐ์์, ์ ๋ต(text)๋ฅผ ๋ง์ถ๋ ๋ชจ๋ธ์ ๋ง๋๋ ๊ฒ
- ์ ๋ต์ ํต์งธ๋ก ๋ง์ถ๋ ๊ฒ์ด ์๋๋ผ, ํ ํฐํ๋ ๊ฒ์ ๋งจ ์ ๋จ์ด์, ๋งจ ๋ท ๋จ์ด์ 
- ํ ํฐํ๋ ์ ๋ต์ ['[CLS]', 'saint', 'bern', '##ade', '##tte', 'sou', '##bir', '##ous', '[SEP]'] ์ธ๋ฐ, ์ฌ๊ธฐ์ saint์ ํด๋นํ๋ ์์น์ ##ous์ ํด๋นํ๋ ์์น๋ฅผ ๋ง์ถ๋ ๋ฒํธ ๋ชจํ์ ํ์ธํ๋ ํ๋ ค ํ๋ ๊ฒ

๊ทธ๋์ ๋ฐ์ convert_data ํจ์์์, ์ ๋ต(text) ๊ธธ์ด๋งํผ ๋ฌธ์ฅ(context)๋ฅผ ์ฌ๋ผ์ด๋ฉ ํ๋ฉด์ ๋ง์ฝ์ ๋ฌธ์ฅ์ด ์ ๋ต์ ํฌํจํ๋ ์์น์ ๋๋ฌํ๋ฉด, ๋ฌธ์ฅ์์ ์ ๋ต์ ๋งจ ์์ด ์ฐ๋ฆฌ๊ฐ ์์ธกํ  1๋ฒ์งธ ์ ๋ต, ์ ๋ต์ ๋งจ ๋ค๊ฐ ์ฐ๋ฆฌ๊ฐ ์์ธกํ  2๋ฒ์งธ ์ ๋ต์ด ๋๊ฒ ๋ฉ๋๋ค.

### โบ๏ธ Train the model 
#### โป Input 
- ์ด 2๊ฐ
- ์ฒซ๋ฒ์งธ ์ธํ์ ํ ํฐํ ๋ ๊ฒ์ด ์ธ๋ฑ์ฑ๋์ด ์ซ์๋ก ๋ณํ๋ ๊ฒ
- ๋๋ฒ์งธ ์ธํ์ ์๋ฌธ์ฅ์ธ์ง ๋ท๋ฌธ์ฅ์ธ์ง ์๋ ค์ฃผ๋ ์ซ์ 
- ํฌ์ง์ : ๋จ์ด ์์์ ๋ฐ๋ผ์ ์๋์ผ๋ก ๋ถ์ฌ๋ฉ๋๋ค.

#### โป Model architecture [2]
Training์ False๋ก ๋์ด์ Bert ๋ชจ๋ธ์์, ๋ง์ง๋ง ํธ๋์คํฌ๋จธ ๊ณ์ธต๊น์ง๋ง ๋ชจ๋ธ์ด ๋ก๋๋๊ฒ ํจ (12์ธต์ ํธ๋์คํฌ๋จธ ๊ณ์ธต)

<img width="1167" alt="Screen Shot 2022-05-31 at 12 09 25" src="https://user-images.githubusercontent.com/40614421/171085135-8d6e4a28-a3f5-4354-b867-a7c89c04f324.png">

#### โป Call Bert 
<img width="1162" alt="Screen Shot 2022-05-31 at 12 19 34" src="https://user-images.githubusercontent.com/40614421/171086132-b803bbbe-b0ba-42b1-bbaa-04287634ca13.png">

BERT ๋ชจ๋ธ์ ์ถ๋ ฅํ๋ ํจ์๋ฅผ ์ง์ ํ๊ณ , start_answer, end_answer๋ฅผ ์์ธก

<img width="1168" alt="Screen Shot 2022-05-31 at 12 24 07" src="https://user-images.githubusercontent.com/40614421/171086581-83bd7f74-71ac-483a-88ac-721b4b47a455.png">

๋ฒํธ ๋ชจํ์ ๋ค์ ํ๋ จ์ํค๋๋ฐ, ์ด๋ฒ์๋ validation_split์ ์๋ ฅํ์ง ์์์ ์ ์ฒด ๋ฐ์ดํฐ๊ฐ ํ๋ จ ๋๋๋ก ๋ง๋ค์ด ์ค

<img width="1159" alt="Screen Shot 2022-05-31 at 12 25 09" src="https://user-images.githubusercontent.com/40614421/171086695-6b89fb72-847b-4c79-b650-b0b66fec02e8.png">

### โบ๏ธ Predict w/ test datasets
- KorQUAD ๋ฐ์ดํฐ ์์์ test ์ฉ๋๋ก ์ฐ์ด๋ dev ํ์ผ์ PANDAS DATAFRAME ํ์์ผ๋ก ๋ถ๋ฌ์ค๋ ํจ์๋ฅผ ์ ์ํจ
- Test์ ๊ฒฝ์ฐ, train ๋ฐ์ดํฐ์ ๋ชจ์์ด ์ฝ๊ฐ ๋ค๋ฅด๊ธฐ ๋๋ฌธ์ ํจ์๋ฅผ ์๋กญ๊ฒ ์ ์
- 
#### โป Test data
ํ์คํธ ๋ฐ์ดํฐํ์ธ 

<img width="1160" alt="Screen Shot 2022-05-31 at 12 26 50" src="https://user-images.githubusercontent.com/40614421/171086854-4ecb41c9-1b1a-45fb-9358-fd074705eee1.png">

#### โป Prediction 
<img width="1173" alt="Screen Shot 2022-05-31 at 12 30 33" src="https://user-images.githubusercontent.com/40614421/171087202-c90f549e-c1f3-44b8-9601-4b586c00ce4e.png">

<img width="1110" alt="Screen Shot 2022-05-31 at 12 31 00" src="https://user-images.githubusercontent.com/40614421/171087248-88ad242f-1fa9-48f0-9ac9-d42528d3686a.png">

### โบ๏ธ ๊ฒฐ๊ณผ ํ์ธ 

<img width="1168" alt="Screen Shot 2022-05-31 at 12 28 24" src="https://user-images.githubusercontent.com/40614421/171086973-5169e4b4-d0ce-44d3-8054-d64a313a39c0.png">

### โบ๏ธ Reference
- [1] [KorQuAD](https://korquad.github.io/KorQuad%201.0/)
- [2] [publicservant_AI(๊ณต๋ฌด์ AI)](https://github.com/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
- [2-1] [Colab:publicservant_AI(๊ณต๋ฌด์ AI)](https://colab.research.google.com/github/kimwoonggon/publicservant_AI/blob/master/05_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_KorQuAD(%ED%95%9C%EA%B5%AD%EC%96%B4_Q%26A)_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
- [3] [๋ฅ๋ฌ๋ ์์ฐ์ด์ฒ๋ฆฌ : BERT ์ดํดํ๊ธฐ](https://www.youtube.com/watch?v=30SvdoA6ApE)
- [4] [BERT๋ก Q&A ๊ตฌํํด๋ณด๊ธฐ With SQuAD AND KERAS](https://www.youtube.com/watch?v=LuApA264Wbs)
- [4-1] [์ผ๋ผ์ค๋ก Q&A ๊ตฌํํ๊ธฐ w/ SQUAD](https://github.com/kimwoonggon/publicservant_AI/blob/master/(Uncased_Squad_V1_1)_%EC%BC%80%EB%9D%BC%EC%8A%A4%EB%A1%9C_Q%26A_%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0.ipynb)
