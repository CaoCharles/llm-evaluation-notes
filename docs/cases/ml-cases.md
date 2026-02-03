# 傳統 ML 案例

本文分享傳統機器學習模型評測的參考案例。

## 案例一：分類模型評測

### 背景

- **任務**：意圖分類
- **類別數**：50+
- **樣本量**：100,000+

### 評測指標

| 指標 | 說明 | 公式 |
|------|------|------|
| Accuracy | 整體準確率 | 正確/總數 |
| Precision | 精確率 | TP/(TP+FP) |
| Recall | 召回率 | TP/(TP+FN) |
| F1 | 調和平均 | 2PR/(P+R) |

### 混淆矩陣分析

```python
from sklearn.metrics import classification_report

report = classification_report(
    y_true, 
    y_pred, 
    output_dict=True
)
```

---

## 案例二：NER 模型評測

### 評測方法

```yaml
ner_evaluation:
  entity_level:
    - exact_match
    - partial_match
    
  token_level:
    - precision
    - recall
    - f1
```

### 結果示例

| 實體類型 | Precision | Recall | F1 |
|----------|-----------|--------|-----|
| PERSON | 0.95 | 0.92 | 0.93 |
| ORG | 0.88 | 0.85 | 0.86 |
| LOCATION | 0.92 | 0.90 | 0.91 |

---

## 案例三：相似度模型

### Embedding 評測

```python
evaluation_tasks = [
    "句子相似度",
    "語義搜索",
    "聚類品質",
]

metrics = {
    "similarity": ["spearman", "pearson"],
    "retrieval": ["MRR", "NDCG", "Recall@K"],
    "clustering": ["silhouette", "NMI"],
}
```

---

## 與 LLM 評測對比

| 維度 | 傳統 ML | LLM |
|------|---------|-----|
| 指標 | 精確客觀 | 多維主觀 |
| 效率 | 快速 | 較慢 |
| 成本 | 低 | 高 |
| 解釋性 | 強 | 弱 |

---

## 經驗總結

!!! success "傳統 ML 評測要點"
    1. 資料集劃分嚴謹
    2. 多指標綜合評估
    3. 關注類別不平衡
    4. 建立可重複的評測流程
