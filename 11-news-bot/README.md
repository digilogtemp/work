# 아이펠캠퍼스 온라인4기 피어코드리뷰[23.05.26]
---
- 코더 : 신인수
- 리뷰어 : 부석경
---
## PRT(PeerReviewTemplate)
---
### [x] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?  
* 원문 : six year old homeless girl allegedly kidnapped raped year old man drug delhi police said found lying pool blood admitted hospital critical condition delhi commission women chief swati maliwal visited said bad condition 
* 실제 요약 : year old homeless girl raped by drug addict in delhi 
* 예측 요약 :  man arrested for raping woman for her in delhi

위와 같이 요약이 성공적으로 진행됐습니다. epoch를 5번돌려 (파파고변역이.)이상한 결과도 섞여있습니다. 
또한 추출요약 또한 확인 했습니다.

그러나 결과에 대한 분석이 빠져있습니다. 
### [o] 주석을 보고 작성자의 코드가 이해되었나요?  
코드마다 주석이 추가되어 코드를 이해하는 데에 있어서 어려움은 없었습니다.
### [x] 코드가 에러를 유발할 가능성이 있나요?  
없습니다. 
### [o] 코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)  
저는 map에 익숙하지 않아서 for문과 map의 차이를 질문했습니다. map의 예측 가능성을 주제로 설명해주셨습니다.

### [x] 코드가 간결한가요?  
```python
clean_text = []

for text in data['text']:
    clean_text.append(preprocess_sentence(text))

#------------------------변경---------------------------
clean_text = list(map(preprocess_sentence, data['text']))

```
for문을 map으로 변경할 수 있습니다.

---
## 참고 링크 및 코드 개선  
