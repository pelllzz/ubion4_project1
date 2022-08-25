### 데이터 관련
- 통계청, K-MBS, KB부동산 등을 통해 데이터를 획득함
- K-MBS의 경우 데이터 양이 방대해서 몇 번에 걸쳐 나눠 받음
######
- 주택 관련 지수 : KB부동산
- 소비자 물가 지수, 실업자 통계 : 통계청
- MBS 관련 데이터 : K-MBS

### 코드 관련 (220825_수정)
- 기존 작업 코드는 code_old 폴더로 따로 뺐습니다
- '전처리_1차.ipynb'와 '전처리_2차_0818.ipynb'를 통해 나눠 하던 것을 code 폴더의 '전처리_ALL.ipynb'로 합쳤습니다
- 기존 분석 코드인 '본격_분석.ipynb'를 정리 차원에서 'analysis.ipynb'로 다시 만들었습니다.

### 커스텀 라이브러리 관련
- 함수 몇 개를 패키지로 따로 빼서 활용하는 것을 고려 중 (클래스는 아직)
- test_package에 아래와 같은 기능이 일단 구현되어 있습니다.

#### 커스텀 라이브러리 내용
- 최적 알파를 찾기 위한 GridSearch를 수행하는 'find_best_alpha'
- def find_best_alpha(type, data, target)
- type : 'ridge', 'lasso', 'elastic' (현재는 소문자만 가능)
- data : feature data
- target : target data
######
- Ridge, Lasso, ElasticNet의 MSE, RMSE 스코어 계산하는 'score_checker'
- def score_checker(type, data, target, alpha)
- type : 'ridge', 'lasso', 'elastic' (현재는 소문자만 가능)
- data : feature data
- target : target data
- alpha : 알파값 입력
######
- 'score_checker'를 좀 더 편리하게 쓰려고 만들었던 'score_many_checker' (수정 필요할듯)
- def score_many_checker(data, target, alpha_ridge, alpha_rasso, alpha_elastic)
- data : feature data
- target : target data
- alpha_ridge : 릿지 알파값
- alpha_rasso : 라쏘 알파값
- alpha_elastic : 엘라스틱넷 알파값
######
- VIF 계산을 위한 함수 'find_vif'
- def find_vif(data)
- data : feature data
######
- 알파의 변화에 따른 feature 영향력을 보기 위한 'check_coeff' 함수
- 이 함수는 변수 그래프까지 그려줍니다
- def check_coeff(type, data, target, alpha)
- type : 'ridge', 'lasso', 'elastic' (현재는 소문자만 가능)
- data : feature data
- target : target data
- alpha는 alpha = [0.1, 0.01, 0.5, 1, 10] 과 같이 5개만!!!! 리스트 정의를 먼저 수행한 다음 사용할 것 (이건 기능 구현 생각해봐야할듯)