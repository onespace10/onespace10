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
# - (Bagging): DecisionTree . RandomForest 배깅 여러개의 활용하고 샘플 중복 생성을 통해 결과 도출
# - (Boosting): , . XGBoost, LGBM

# 4) 랜덤포레스트(RandomForest)
# ** Hyperparameter** 주요
# - random_state: . ! 랜덤 시드 고정 값 고정해두고 튜닝할 것
# - n_jobs: CPU 사용 갯수
# - max_depth: . 깊어질 수 있는 최대 깊이 과대적합 방지용
# - n_estimators: 앙상블하는 트리의 갯수
# - max_features: feature . 최대로 사용할 의 갯수 과대적합 방지용
# - min_samples_split: . default=2. 트리가 분할할 때 최소 샘플의 갯수 과대적합 방지용

from sklearn.ensemble import RandomForestClassifier
rfc = RandomForestClassifier(n_estimators=3, random_state=42)
rfc.fit(X_train, y_train)
rfc_pred = rfc.predict(X_test)
recall_eval('RandomForest Ensemble', rfc_pred, y_test)

```

```
# 5) XGBoost
# + DecisionTree Strong Learner Boosting 여러개의 를 결합하여 만드는 앙상블 기법
# ** Hyperparameter** 주요
# - random_state: . ! 랜덤 시드 고정 값 고정해두고 튜닝할 것
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
# + XGBoost DecisionTree Boosting 와 함께 주목받는 알고리즘 기반의 앙상블 기법
# + XGBoost . 에 비해 학습시간이 짧은 편이다

# ** ** 주요 특징
# - scikit-learn . 패키지가 아닙니다
# - 성능이 우수함
# - . 속도도 매우 빠릅니다

# ** Hyperparameter** 주요
# - random_state: . ! 랜덤 시드 고정 값 고정해두고 튜닝할 것
# - n_jobs: CPU 사용 갯수
# - learning_rate: 학습율. 너무 큰 학습율은 성능을 떨어뜨리고 너무 작은 학습율은 학습이 느리다 적절한 값을 찾아야함 와 같이 튜닝
# - n_estimators: . ( ). default=100 부스팅 스테이지 수 랜덤포레스트 트리의 갯수 설정과 비슷한 개념
# - max_depth: 트리의 깊이 과대적합 방지용. default=3. 
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

1.  (DNN) 딥러닝 심층신경망 모델 프로세스

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
batch_size = 16
epochs = 20

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
