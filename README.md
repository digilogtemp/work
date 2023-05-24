# 아이펠캠퍼스 온라인4기 피어코드리뷰[23.05.24]
---
- 코더 : 신인수
- 리뷰어 : 부석경
---
## PRT(PeerReviewTemplate)
---
[x] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?  
> 1537/1537 - 5s - loss: 0.8834 - accuracy: 0.8465   
> [0.8833787441253662, 0.8464511632919312]   
정확도 85%를 달성하지 못했습니다.

LSTM, CNN, GlobalMaxPooling1D 세가지 모델을 분석했습니다.

[o] 주석을 보고 작성자의 코드가 이해되었나요?  
```python
# earlystopping을 이용해서 과적합을 방지
from keras.callbacks import EarlyStopping
es=EarlyStopping(monitor='val_loss',mode='min',verbose=1,patience=10)
```
추가한 코드에 대하여 주석으로 설명을 달아주어 이해하기 쉬웠습니다.

[x] 코드가 에러를 유발할 가능성이 있나요?  
* 찾지 못했습니다.   
   
[o] 코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)  

* [Early stopping](https://keras.io/api/callbacks/early_stopping/)에 관해 질문했는데 자세히 답변해 주셨습니다.  
  
[x] 코드가 간결한가요?  
```python
# "bo"는 "파란색 점"입니다
plt.plot(epochs, loss, 'bo', label='Training loss')
# b는 "파란 실선"입니다
plt.plot(epochs, val_loss, 'b', label='Validation loss')
plt.title('Training and validation loss')
plt.xlabel('Epochs')
plt.ylabel('Loss')
plt.legend()

plt.show()
```
그래프를 나타내기 위한 코드가 길거니와 반복적으로 나타나 함수로 지정해주면 더욱 좋을것 같습니다.

---
## 참고 링크 및 코드 개선  
```python
def show_loss_acc_graph(loss, acc,val_loss, val_acc, epochs, graph_title='Loss and Accuracy'):

    fig, ax = plt.subplots(1,2, figsize=(10, 5))
    
    ax[0].plot(epochs, loss, 'b--', label='Training loss')
    ax[0].plot(epochs, val_loss, 'b', label='Validation loss')
    ax[0].set_title('Training and validation loss')
    ax[0].set_xlabel('Epochs')
    ax[0].set_ylabel('Loss')
    ax[0].legend()

    ax[1].plot(epochs, acc, 'b--', label='Training acc')
    ax[1].plot(epochs, val_acc, 'b', label='Validation acc')
    ax[1].set_title('Training and validation accuracy')
    ax[1].set_xlabel('Epochs')
    ax[1].set_ylabel('Accuracy')
    ax[1].legend()
    
    fig.suptitle(graph_title, fontsize=16)

    plt.show()
```
