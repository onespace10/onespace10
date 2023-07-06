# python에서 df.select_dtypes('object').columns과 df.select_dtypes('object').columns.values 두 차이

```
# df.select_dtypes('object').columns ☜ Series
0    name
1    age
2    gender
Name: columns, dtype: object
```

```
# df.select_dtypes('object').columns.values ☜ ndarray
['name', 'age', 'gender']
```

# Library 모음

## 머신러닝

1. 머신러닝 모델 프로세스

   ① 라이브러리 임포트(import)

   ② 데이터 가져오기 (Loading the data)

   ③ 탐색적 데이터 분석 (Exploratory Data Analysis)

   ④ 데이터 전처리(Data PreProcessing) : 데이터 타입 변환, Null 데이터 처리, 누락데이터 처리, 더미 특성 생성, 특성 추출 (feature engineering) 등

   ⑤ Train, Test 데이터셋 분할

   ⑥ 데이터 정규화(Normalizing the Data)

   ⑦ 모델 개발 (Creating the Model)

   ⑧ 모델 성능 평가
2. 평가 지표 활용: 모델별 성능 확인을 위한 함수 (가져다 쓰면 된다)
3. 단일 회귀예측 모델: LogisticRegression, KNN, DecisionTree
4. 앙상블(Ensemble) : RandomForest, XGBoost, LGBM
5. 재현율 성능이 너무 안나온다. 어떻게 할 수 있을까?

```
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, stratify = y, random_state=42)

```

```
# Standard Scaling 적용
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X_train)
X_train = scaler.transform(X_train)
```

```
# MinMaxScaler 적용
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

```
#  1) 로지스틱 회귀(LogisticRegression, 분류) 
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import confusion_matrix, classification_report, accuracy_score, precision_score, recall_score, f1_score
lg = LogisticRegression()
lg.fit(X_train, y_train)
lg.score(X_test, y_test)
lg_pred = lg.predict(X_test)
confusion_matrix(y_test, lg_pred)
accuracy_score(y_test, lg_pred)
precision_score(y_test, lg_pred)
recall_score(y_test, lg_pred)
f1_score(y_test, lg_pred)
recall_eval('LogisticRegression', lg_pred, y_test)

```

```
#  2) KNN (K-Nearest Neighbor)
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)
knn_pred = knn.predict(X_test)
recall_eval('K-Nearest Neighbor', knn_pred, y_test)

```

```
# 3) 결정트리(DecisionTree)
from sklearn.tree import DecisionTreeClassifier
dt = DecisionTreeClassifier(max_depth=10, random_state=42)
dt.fit(X_train, y_train)
dt_pred = dt.predict(X_test)
recall_eval('DecisionTree', dt_pred, y_test)

```

```
# ** 앙상블 기법의 종류
# - 배깅(Bagging): 여러개의 DecisionTree 활용하고 샘플 중복 생성을 통해 결과 도출. RandomForest  
# - 부스팅(Boosting): 약한 학습기를 순차적으로 학습을 하되, 이전 학습에 대하여 잘못 예측된 데이터에 가중치를 부여해 오차를 보완해 나가는 방식. XGBoost, LGBM

# 4) 랜덤포레스트(RandomForest)
#    Bagging 대표적인 모델로써, 훈련셋트를 무작위로 각기 다른 서브셋으로 데이터셋을 만들고 여러개의 DecisionTree로 학습하고 다수결로 결정하는 모델
# ** Hyperparameter** 주요
# - random_state: 랜덤 시드 고정 값 고정해두고 튜닝할 것!
# - n_jobs: CPU 사용 갯수
# - max_depth: 깊어질 수 있는 최대 깊이 과대적합 방지용.
# - n_estimators: 앙상블하는 트리의 갯수
# - max_features: 최대로 사용할 feature의 갯수 과대적합 방지용.
# - min_samples_split: 트리가 분할할 때 최소 샘플의 갯수. default=2. 과대적합 방지용

from sklearn.ensemble import RandomForestClassifier
rfc = RandomForestClassifier(n_estimators=3, random_state=42)
rfc.fit(X_train, y_train)
rfc_pred = rfc.predict(X_test)
recall_eval('RandomForest Ensemble', rfc_pred, y_test)

```

```
# 5) XGBoost
# +  여러개의 DecisionTree를 결합하여 Strong Learner 만드는 Boosting 앙상블 기법
# ** Hyperparameter** 주요
# - random_state: 랜덤 시드 고정 값 고정해두고 튜닝할 것.!
# - n_jobs: CPU 사용 갯수
# - learning_rate: 학습율. 너무 큰 학습율은 성능을 떨어뜨리고 너무 작은 학습율은 학습이 느리다 적절한 값을 찾아야함 와 같이 튜닝
# - n_estimators: . ( ). default=100 부스팅 스테이지 수 랜덤포레스트 트리의 갯수 설정과 비슷한 개념
# - max_depth: . . default=3. 트리의 깊이 과대적합 방지용
# - subsample: . . default=1.0 샘플 사용 비율 과대적합 방지용
# - max_features: feature . . default=1.0

from xgboost import XGBClassifier
xgb = XGBClassifier(n_estimators=3, random_state=42)
xgb.fit(X_train, y_train)
xgb_pred = xgb.predict(X_test)
recall_eval('XGBoost', xgb_pred, y_test)

```

```
# 6) Light GBM
# + XGBoost와 함께 주목받는 DecisionTree Boosting 알고리즘 기반의 앙상블 기법
# + XGBoost에 비해 학습시간이 짧은 편이다. 

# ** ** 주요 특징
# - scikit-learn 패키지가 아닙니다.
# - 성능이 우수함
# - 속도도 매우 빠릅니다.

# ** Hyperparameter** 주요
# - random_state: 랜덤 시드 고정 값 고정해두고 튜닝할 것. ! 
# - n_jobs: CPU 사용 갯수
# - learning_rate: 학습율. 너무 큰 학습율은 성능을 떨어뜨리고, 너무 작은 학습율은 학습이 느리다 적절한 값을 찾아야함 와 같이 튜닝. default=0.1
# - n_estimators: 부스팅 스테이지 수. (랜덤포레스트 트리의 갯수 설정과 비슷한 개념). default=100 
# - max_depth: 트리의 깊이. 과대적합 방지용. default=3. 
# - colsample_bytree: 샘플 사용 비율 (max_features와 비슷한 개념). 과대적합 방지용. default=1.0

from lightgbm import LGBMClassifier
lgbm = LGBMClassifier(n_estimators=3, random_state=42)
lgbm.fit(X_train, y_train)
lgbm_pred = lgbm.predict(X_test)
recall_eval('LGBM', lgbm_pred, y_test)
lgbm.score(X_test, y_test)
recall_score(y_test, lgbm_pred)

```

## 딥러닝

1. (DNN) 딥러닝 심층신경망 모델 프로세스

   - 데이터 가져오기
   - 데이터 전처리
   - Train, Test 데이터셋 분할
   - 데이터 정규화
   - DNN 딥러닝 모델
2. 재현율 성능이 좋지 않다. 어떻게 성능향상 할 수 있나?

(DNN) 딥러닝 심층신경망 모델 프로세스

    ① 라이브러리 임포트(import)

    ② 데이터 가져오기(Loading the data)

    ③ 탐색적 데이터 분석(Exploratory Data Analysis)

    ④ 데이터 전처리(Data PreProcessing) : 데이터타입 변환, Null 데이터 처리, 누락데이터 처리, 더미특성 생성, 특성 추출 (feature engineering) 등

    ⑤ Train, Test 데이터셋 분할

    ⑥ 데이터 정규화 (Normalizing the Data)

    ⑦ 모델 개발(Creating the Model)

    ⑧ 모델 성능 평가

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv('data_save.csv)
df['Churn'].value_counts().plot(kind='bar') ☜ 데이터 불일치
cal_cols = df.select_dtypes('object').columns.values ☜ 범주형 데이터 get_dummies 함수 활용하여 One-Hot-Encoding
df1 = pd.get_dummies(data=df, columns=cal_cols)

```

```
from sklearn.model_selection import train_test_split
X = df1.drop('Churn', axis=1).values
y = df1['Churn'].values

```

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, stratify=y, random_state=42)
```

```
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

```

```
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout
tf.random.set_seed(100)
batch_size = 16  ☜ # 하이퍼파라미터 설정: batch_size, epochs 
epochs = 20

```

```
# Sequential() 모델 정의 하고 model로 저장
# input layer는  input_shape=() 옵션을 사용한다. 
# 39개 input layer 
# unit 4개 hidden layer 
# unit 3개 hidden layer 
# 1개 output layser : 이진분류

model = Sequential()
model.add(Dense(4, activation = 'relu', input_shape = (39,)))
model.add(Dense(3, activation = 'relu'))
model.add(Dense(1, activation = 'sigmoid'))

```

```
    1)모델 구성 과적합 방지
    model = Sequential()
    model.add(Dense(4, activation='relu', input_shape=(39,)))
    model.add(Dropout(0.3))
    model.add(Dense(3, activation='relu'))
    model.add(Dropout(0.3))
    model.add(Dense(1, activation='sigmoid'))

```

    2)DNN 모델을 학습(모델 이름 : model, epoch : 10번, batch_size : 10번)_Sequential 모델의 fit() 함수 사용

```
    model.fit(X_train, y_train, validation_data=(X_test, y_test), epochs=10, batch_size=10)

```

    3)DNN 모델을 학습(모델 이름 : model,  39 input layer, unit 5개 hidden layer, dropout, unit 4개 hidden layer, dropout, 2개 output layer : 다중분류)

```
    model = Sequential()
    model.add(Dense(5, activation='relu', input_shape=(39,)))
    model.add(Dropout(0.3))
    model.add(Dense(4, activation='relu'))
    model.add(Dropout(0.3))
    model.add(Dense(2, activation='softmax'))

```

    4)DNN 모델을 학습(모델 이름 : model,  13 input layer, unit 5개 hidden layer, dropout, unit 4개 hidden layer, dropout, 2개 output layer : 이진분류)

```
    model = Sequential()
    model.add(Dense(5, activation='relu', input_shape=(13,)))
    model.add(Dropout(0.3))
    model.add(Dense(4, activation='relu'))
    model.add(Dropout(0.3))
    model.add(Dense(2, activation='softmax'))  
```

```
model.summary()  ☜ # 모델 확인
```

```
# 모델 컴파일 - 이진 분류 모델
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# 모델 컴파일 - 다중 분류 모델 (Y값을 One-Hot-Encoding 한 경우)
# model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

# 모델 컴파일 - 다중 분류 모델 (Y값을 One-Hot-Encoding 하지 않은 경우)
# model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

# 모델 컴파일 - 예측 모델
# model.compile(optimizer='adam', loss='mse')

```

```
# 모델 학습
history = model.fit(X_train, y_train, validation_data=(X_test, y_test), epochs=20, batch_size=16)
```

### Callback : , 조기종료 모델 저장

```
from tensorflow.keras.callbacks import EarlyStopping, ModelCheckpoint

```

```
# val_loss 모니터링해서 성능이 5번 지나도록 좋아지지 않으면 조기 종료
early_stop = EarlyStopping(monitor='val_loss', mode='min', verbose=1, patience=5)

```

```
# val_loss 가장 낮은 값을 가질때마다 모델저장
check_point = ModelCheckpoint('best_model.h5', verbose=1, monitor='val_loss', mode='min', save_best_only=True)

```

```
# 모델 학습
history = model.fit(x=X_train, y=y_train, epochs=50 , batch_size=20, validation_data=(X_test, y_test), verbose=1, callbacks=[early_stop, check_point])

```

### 모델 성능 평가

```
losses = pd.DataFrame(model.history.history)

```

```
# 성능 시각화
losses[['loss','val_loss']].plot()
losses[['loss','val_loss', 'accuracy','val_accuracy']].plot()
plt.plot(history.history['accuracy'])
plt.plot(history.history['val_accuracy'])
plt.title('Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Acc')
plt.legend(['acc', 'val_acc'])
plt.show()

```

```
# 성능 평가
from sklearn.metrics import classification_report, accuracy_score, precision_score, recall_score, f1_score
pred = model.predict(X_test)
y_pred = np.argmax(pred, axis=1)
accuracy_score(y_test, y_pred)
recall_score(y_test, y_pred)

# accuracy, recall, precision 성능 한번에 보기
print(classification_report(y_test, y_pred))

```

### 모델 성능 개선

재현율이 좋지 않을 때

1)DNN 하이퍼 파라미터 수정

2)Feature Engineering 통한 성능향상

    - 불균형 'Churn' 데이터 균형 맞추기 : OverSampling, UnderSampling
    - OverSampling 기법 : SMOTE(Synthetic Minority Over-sampling Technique)

```
# imbalanced-learn 패키지 설치
get_ipython().system('pip install -U imbalanced-learn')

```

```
# SMOTE 함수 이용하여 Oversampling 
from imblearn.over_sampling import SMOTE
smote = SMOTE(random_state=0)
X_train_over, y_train_over = smote.fit_resample(X_train, y_train)
print('SMOTE / : ' 적용 전 학습용 피처 레이블 데이터 세트 , X_train.shape, y_train.shape)
print('SMOTE / : ' 적용 후 학습용 피처 레이블 데이터 세트 , X_train_over.shape, y_train_over.shape)

# SMOTE : 0 1 적용 후 레이블 값 분포 과 갯수가 동일
pd.Series(y_train_over).value_counts()

# 데이터 정규화
# MinMaxScaler
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
scaler.fit(X_train)
X_train_over = scaler.transform(X_train_over)
X_test = scaler.transform(X_test)

X_train_over.shape, y_train_over.shape, X_test.shape, y_test.shape


```

### 모델 개발(Creating the Model)

```
model = Sequential()
model.add(Dense(64, activation='relu', input_shape=(39,)))
model.add(Dropout(0.3))
model.add(Dense(32, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(16, activation='relu'))
model.add(Dropout(0.3))
model.add(Dense(2, activation='softmax'))

```

```
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
```

```
from tensorflow.python.keras.callbacks import EarlyStopping
# 여기서는 val_accuracy 모니터링해서 성능이 좋아지지 않으면 조기 종료 하게 함. 
early_stop = EarlyStopping(monitor='val_accuracy', mode='max', verbose=1, patience=5)
```

```
from tensorflow.python.keras.callbacks import ModelCheckpoint
check_point = ModelCheckpoint('best_model.h5', verbose=1, monitor='val_loss', mode='min', save_best_only=True)
```

```
history = model.fit(x=X_train_over, y=y_train_over, epochs=50 , batch_size=32, validation_data=(X_test, y_test), verbose=1, callbacks=[early_stop, check_point])

```

## 개발 모델 성능 평가

```
losses = pd.DataFrame(model.history.history)
```

```
# 성능 시각화
losses[['loss','val_loss']].plot()
losses[['loss','val_loss', 'accuracy','val_accuracy']].plot()

plt.plot(history.history['accuracy'])
plt.plot(history.history['val_accuracy'])
plt.title('Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Acc')
plt.legend(['acc', 'val_acc'])
plt.show()

```

```
# 성능 평가
from sklearn.metrics import classification_report, accuracy_score, precision_score, recall_score, f1_score
pred = model.predict(X_test)
y_pred = np.argmax(pred, axis=1)
accuracy_score(y_test, y_pred)
recall_score(y_test, y_pred)

# accuracy, recall, precision 성능 한번에 보기
print(classification_report(y_test, y_pred))
```

# df.drop('customerID', axis=1, inplace=True)

# '',  ' ' 찾기

```
cond = (df['TotalCharges'] == '') | (df['TotalCharges'] == ' ')`
```

# DataFrame replace 함수

```
df['Churn'].replace(['Yes', 'No'], [1, 0], inplace=True)
```

# 컬럼 삭제

```
df.drop('DeviceProtection', axis=1, inplace=True)
df.reset_index(drop = True)
```

# Null 여부 확인

```
df.isnull().sum()
```

# df 데이터프레임의 'Pa'컬럼의 값 분포를 구하고 Bar차트

```
df['Pa'].value_counts().plot(kind='bar')
```

# 한꺼번에 Bar 차트 확인

```
object_list = df.select_dtypes('object').columns.values
for col in object_list:
	df[col].value_counts().plot(kind='bar')
	plt.title(col)
	plt.show()
```

# number(int, float) 컬럼에 대해 분포 확인

```
df.select_dtypes('number')
df['Churn'].value_counts().plot(kind='bar') ☜ 'Chun'컬럼은 0, 1되어 있으므로
```

# bar graph와 histplot 차이

```
둘 다 데이터의 빈도를 시각화 한다.
막대 그래프는 범주형 데이터 시각화에 쓰인다.
히스토그램은 연속형 데이터 시각화에 쓰인다.
```

# TotalCharges ( ) 서비스 총요금 에 대한 히스토그램

```
# 처음에 많이 사용하고 금액이 커질수록 사용자수가 줄어든다
sns.histplot(data=df, x='TotalCharges')
```

# kdeplot : 히스토그램을 곡선으로

```
sns.kdeplot(data=df, x='TotalCharges', hue='Churn')
```

# heatmap ['tenure','MonthlyCharges','TotalCharges'] 컬럼간의 상관관계

```
df[['tenure','MonthlyCharges','TotalCharges']].corr()
그림으로
sns.heatmap(df[['tenure','MonthlyCharges','TotalCharges']].corr(), annot=True)
```

# astype

```
df = df.astype({' ' 시도코드 :'str', ' ' 성별코드 :'str'})
```

# sklearn.MinMaxScaler() 스케일링에서 fit(), transform(), MinMaxScaler() 세 메서드의 차이점

| fit()           | 데이터에 대한 통계를 계산하여 모델을 학습합니다.       |
| --------------- | ------------------------------------------------------ |
| transform()     | 데이터를 모델의 학습된 통계를 사용하여 스케일링합니다. |
| fit_transform() | fit() 메서드와 transform() 메서드를 모두 한 번에 실행  |

# fillna() 적용

df['Age'].fillna(df['Age'].mean(),inplace=True)

# StandardScaler()와 MinMaxScaler()는 모두 데이터를 스케일링하는 데 사용되는 변환기 클래스 차이점
| 특징	| StandardScaler()	| MinMaxScaler() |
|---------------|--------------------|----------------------------|
| 데이터 변환	| 평균 0, 표준 편차 1	| 최소값 0, 최대값 1|
| 적합한 알고리즘	| 대부분의 머신 러닝 알고리즘	| k-최근접 이웃 알고리즘 등|
| | 정규분포 변환 | 특정 범위 변환|

```

```
