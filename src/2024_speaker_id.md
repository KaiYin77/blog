# 你需要懂的語音驗證 - Speaker verification

*2024年10月1日 · 閱讀時間約 5 分鐘*

> 學習一個新領域，尤其是深度學習的領域，不外乎以下幾點：該領域目前的發展程度, 面臨到的痛點, 對應的解決方案, 相關的資料集, 評估方法。

今天倒過來說，先從評估方法講起。

## 評估方法

- Equal Error Rate (EER)，核心概念就是窮舉每個閥值所對應的False Positive Rate (FPR) 和 False Negative Rate (FNR)，找到兩者等值時點，業界稱為 Equal Error Rate，跨方法間的比較，EER越小越好。

## 不外乎讓Speaker Embedding或Token具有辨識度

開發循環：

1. Model development
2. Speaker enrollment
3. Online evaluation

> 在Model development這個階段，可以直接想成metric-based meta learning，也就是讓神經網路學習比較query資料（待預測資料）與source資料（類別代表資料）之間的相似程度。

## 資料集 Really Matter
>
> Google認為需要1.8萬個語者、超過36M段話語的資料規模才能讓模型達到好的辨識效果。

- 常見公開資料集：
  - VoxCeleb：1251 位語者、150K 段話語
  - VoxCeleb 2：6112 位語者、1M 段話語

## 方法論脈絡

### ML-based 方法

- 2024年的現在，早已被DL-based方法取代
- 當年最強的ML-based方法是i-vector
- i-vector啟發了DL-based的先驅d-vector

### DL-based 方法

1. d-vector (2018)
   - 在有標注人物的語音上進行分類訓練
   - 抽取最後一層hidden layer作為未來enrollment evaluation的基準
   - 問題：因window size造成視野變小，失去整段音訊前後文

2. x-vector (2018)
   - 解決了d-vector面臨視窗侷限的問題

未來繼續介紹end-to-end的方法。
