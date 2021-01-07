
Cross Validation approach to tune parameters.

Grid Search 함수로 best parameter
여러번 반복해서 best parameter 포함한 model을 training

Result : well을 하나씩 제거하면서 training 해서 F1score 평균


1. XGBClassifier(**)
2. normalize process

7. TPOTClassifier(**)
8. make_pipeline(XGBClassifier(**))


code 2번 중간까지 봄