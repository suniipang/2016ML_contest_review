ISPL team have 4 trial codes.

### Basic process

- Augmentaion

- Split the data set to training, validation and test data

- Parameter optimizaion

- Predict labels on test data



### Try 1 code

Aggregating features at neighboring depths.
: window를 이용해서 neighbor depth의 데이터를 가로로 쭉 이어붙임.

Classification method : RandomForestClassifier + OneVsOneClassifier


### Try 2 code

'NaN' in PE feature. > NaN을 average PE value로 대체 (Imputer)

### Try 3 code

Well마다 depth 기준으로 sorting
Feature augmentation : spatial gradient + high order features

Classification method : GradientBoostingClassifier + OneVsOneClassifier

(추가로 random seed 100개를 통해 scoring에 사용 )

### Try 4 code

Layered Classification : label을 두 구간으로 나누어 각각 모델 훈련
Classification method : XGBClassifier
