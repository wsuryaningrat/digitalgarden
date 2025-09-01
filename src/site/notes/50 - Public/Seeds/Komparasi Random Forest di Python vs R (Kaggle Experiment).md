---
{"dg-publish":true,"permalink":"/50-public/seeds/komparasi-random-forest-di-python-vs-r-kaggle-experiment/"}
---

## Dataset
- ISOT Fake News Dataset
- Jumlah data: 
	- Fake.csv: 17903 x 4
	- True.csv: 20826 x 4
- Preprocessing: gabung `title + text`

## Preparation
Biar adil, gw bikin **2 versi script**:
1. **Versi awal** → Python pakai `TfidfVectorizer`, R pakai `tm::DocumentTermMatrix` (hasilnya beda karena treatment fitur gak sama persis).  
2. **Versi update** → Python (`TfidfVectorizer(max_features=5000, stop_words="english")`) dan R (`text2vec::create_vocabulary` + `prune_vocabulary(vocab_term_max=5000)`) → jadi preparation identik, sama-sama 5000 fitur TF-IDF.  

## Modeling
- **Python** → `sklearn.ensemble.RandomForestClassifier`  
- **R** → `ranger::ranger` (lebih efisien dibanding `randomForest`)  

## Metrics dicatat
- Accuracy  
- F1 score  
- ROC AUC  
- Waktu training  
- RAM usage  

## Hasil

| Test | Language     | Model        | Accuracy | F1    | ROC AUC | Train Time | RAM Usage |
| :--- | :----------- | ------------ | -------- | ----- | ------- | ---------- | --------- |
| 1    | ***Python*** | RF (sklearn) | 0.997    | 0.997 | 0.997   | 52.44s     | 0.06GB    |
| 1    | R            | RF (ranger)  | 0.998    | 0.999 | 0.999   | 97.23s     | 0.05GB    |
| 2    | Python       | RF (sklearn) | tbu      |       |         |            |           |
| 2    | R            | RF (ranger)  |          |       |         |            | tbu       |

## Kesimpulan
- Python lebih efisien memori & lebih cepat.
- R dengan `ranger` masih bisa jalan tapi lebih berat.




`button-publish`
