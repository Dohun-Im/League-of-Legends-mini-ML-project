# League_of_Legends_miniMLproject

**1️⃣  **전처리 - 필요** ❌

**2️⃣  EDA**🤩 

✅  target ⇒ ['blueWins']

✅  상관계수(pearson) 0.2 이상인 columns

blueFirstBlood, blueKills, blueDeaths, blueAssists, blueEliteMonsters, blueDragons, blueTotalGold, blueAvgLevel, blueTotalExperience, blueTotalMinionsKilled, blueGoldDiff, blueExperienceDiff, blueCSPerMin, blueGoldPerMin

✅  우리팀이 쓸 columns ⇒ "features"

blueFirstBlood, blueKills, blueAssists, blueDragons, blueGoldDiff, blueExperienceDiff, blueTotalMinionsKilled 

➕  blueHeralds, blueTowersDestroyed - 임의 추가

✅  최종 features

['KillDiff', 'FirstBlood' , 'AssistDiff', 'GoldDiff', 'Dragon', 'Herald', 'FirstTower', 'ExDiff' , 'MinionDiff']

**3️⃣  Cross Validation, GridSearch**

✅  Cross Validation: Model Selection ⇒ "svc_linear"

1. Train Data
    
    ❌ Random Forest - `0.6940`
    
    ❌ Logistic Regression - `0.7190` 
    
    ❌ KNeighbors(n=5, n=10) - `0.6849`, `0.7003`
    
    ⭕️ Support Vector Clustering(kernel = 'linear', 'rbf') - `0.7168`, `0.7136`
    
2. Test Data
    
    accuracy = `0.7318376068376068`
    

✅  GridSearch

- kernel = "linear"
- C = 0.01
- cv = 5

**4️⃣  Confusion Matrix**

```
              precision    recall  f1-score   support

           0       0.75      0.73      0.74       971
           1       0.72      0.73      0.72       901

    accuracy                           0.73      1872
   macro avg       0.73      0.73      0.73      1872
weighted avg       0.73      0.73      0.73      1872
```

☑️ 고찰

📶 Dataset 

❗️decribe()를 통해 이상치 제거 (1% ~ 99% 데이터 추출) ⇒ 정확도⬆️

❓상관관계 분석하여 feature 선정했지만, feature가 독립적인지, 종속적인지 판단 부족 ⇒ "더 자세한 데이터 상관관계 분석 필요"

🤖 Model

❗️학습데이터를 통한 정확도 < 테스트데이터를 통한 정확도

❗️LogisticRegression과 SupportVectorClustering_Linear의 정확도가 비슷 ⇒ "선형적인 관계성이 강하다."

❓svc_linear의 경우, 시간소요⬆️ , **BUT** 정확도가 가장 높을수도.. ⇒ "데이터수를 줄인다?"

🔢 Parameter

❗️GridSearch를 통해 최적의 parameter 선정

❓ svc_linear의 경우, 시간소요⬆️  ⇒ "데이터수를 줄인다?"
