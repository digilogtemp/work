# 아이펠캠퍼스 온라인4기 피어코드리뷰[23.05.30]
---
- 코더 : 신인수
- 리뷰어 : 정연준
---
## PRT(PeerReviewTemplate)
---
[o] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?  

![image](https://github.com/digilogtemp/work/assets/131635437/c6292d8a-4bf0-41b8-a05a-c18dfb1341e2)

[o] 주석을 보고 작성자의 코드가 이해되었나요?  

```python
#가중치 업데이트 : 하나의 배치 크기만큼 데이터를 입력했을 때 가중치를 1회 업데이트
@tf.function
def train_step(sketch, original):
    with tf.GradientTape() as gene_tape, tf.GradientTape() as disc_tape:
        # Generator 예측
        fake_colored = generator(sketch, training=True)
        # Discriminator 예측
        fake_disc = discriminator(sketch, fake_colored, training=True)
        real_disc = discriminator(sketch, original, training=True)
        # Generator 손실 계산
        gene_loss, l1_loss = get_gene_loss(fake_colored, original, fake_disc)
        gene_total_loss = gene_loss + (100 * l1_loss) ## <===== L1 손실 반영 λ=100
        # Discrminator 손실 계산
        disc_loss = get_disc_loss(fake_disc, real_disc)
                
    gene_gradient = gene_tape.gradient(gene_total_loss, generator.trainable_variables)
    disc_gradient = disc_tape.gradient(disc_loss, discriminator.trainable_variables)
    
    gene_opt.apply_gradients(zip(gene_gradient, generator.trainable_variables))
    disc_opt.apply_gradients(zip(disc_gradient, discriminator.trainable_variables))
    return gene_loss, l1_loss, disc_loss
```

- 각 코드의 출력을 주석으로 간단히 설명해주었습니다.

[o] 코드가 에러를 유발할 가능성이 있나요?  

- 에러의 가능성이 딱히 보이진 않습니다.

[o] 코드 작성자가 코드를 제대로 이해하고 작성했나요? (직접 인터뷰해보기)  

- 코드의 흐름을 이해하고 작성한 듯 합니다.

[o] 코드가 간결한가요?  

더 간결하게 할 여지가 보이지 않습니다.

---
## 참고 링크 및 코드 개선  
