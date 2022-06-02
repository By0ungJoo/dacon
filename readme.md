# Computer Vision 이상치 탐지 알고리즘 경진대회

---

[Computer Vision 이상치 탐지 알고리즘 경진대회](https://dacon.io/competitions/official/235894/overview/description)

모델 : EfficientNet_V2

- timm > efficientnetv2_rw_s
    - Drop out : 0.3
    - optimizer : sam
    - Kfold : 5
    - image set : basic_data + transform_data + abnormal_data
        - transform_data(Horizontal Flip, Rotate, Vertical Flip)
    - image_size : 300*300
    - normalization : imagenet mean / mean > mean = [0.485, 0.456, 0.406], std = [0.229, 0.224, 0.225]

- 결과
    - macro f1-score : 0.84051 (49 / 481)
    
- etc
    - ResNet50 부터 해서 ResNet200, ResNext 마지막으로  EfficientNetV2 까지 basic line을 만들고 확정하는데 생각보다 오랜 시간이 소요되었다. macro f1-score 0.84051, 총 49등으로 순위권에 드는건 실패했지만 처음으로 딥러닝 모델을 만들어보면서 다음에는 기존에 만들어둔 모델을 바탕으로 더 빠르게 옵티마이저 조정이나 새로운 방법을 적용하여 전보다 좋은 결과를 얻을 수 있는 기회가 되었다고 생각했다.
    - 이상치를 보이는 데이터가 정상인 데이터에 비해 턱없이 부족했는데, 이런 심한 데이터 불균형을 해결하는 것이 이번 대회에서 좋은 점수를 얻는 방법이라고 생각하여 이상치 데이터를 추가로 Data Agumentation을 진행했는데, 대회가 끝나고 좋은 결과를 얻은 다른 팀이 공유한 코드를 보고 데이터 불균형을 해결할 수 있는 더 좋은 방법이 있었던 것 같다.(ex.예측 결과가 좋지 않았던 클래스들만 따로 더 학습 후 보팅)
    
각 클래스별 정상/이상 비율
    
![graph](https://user-images.githubusercontent.com/87263584/171583724-099ae954-b5d3-4e23-9ecd-aa1f466af222.png){: width="50%" height="50%"}{: .center}
    
   - 각 이미지의 크기를 300*300으로 했었는데 좋은 결과를 받은 팀들을 보면 거의 대부분이 이미지 크기가 300*300 보다 훨씬 큰 크기로 학습을 진행했다. 각자 가진 컴퓨터의 스펙은 다르겠지만 한정된 리소스에서 최대한 효율적으로 사용할 수 있는 코드 작성 능력이 조금 부족했다고 느끼게 되었고 다음에 다시 대회에 참가하게 되면 이 부분도 주의 깊게 보고 작성해야겠다.
