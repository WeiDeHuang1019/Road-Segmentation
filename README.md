# Road-Segmentation
Road-Segmentation using non-learning-based algorithms.

## 1. 專案概述

本專案旨在以 **傳統影像處理與電腦視覺演算法（non-learning based methods）** 實現道路分割（road segmentation）任務。在不依賴深度學習或機器學習模型的前提下，透過影像前處理、特徵提取與規則式判斷等方法，對輸入的道路影像進行像素級分類，將畫面分割為「道路」與「非道路」兩類。

相較於目前主流的 Learning-Based segmentation 方法（如 CNN、U-Net 等），本專案著重於：

* 降低運算複雜度（computational complexity）
* 提高可解釋性（interpretability）
* 降低對訓練資料與模型的依賴

此外，本方法將特別考量**嵌入式系統（embedded system）部署需求**，包含：

* 演算法時間複雜度（time complexity）
* 記憶體使用（memory footprint）
* 可量化性（quantization feasibility）

最終目標是設計一套在資源受限環境中仍具備實用價值的道路分割方案。

---

## 2. 實驗目標

本專案的核心實驗目標如下：

1. **實現道路分割功能**

   * 輸入：一張道路場景影像（RGB 或灰階）
   * 輸出：對應的 segmentation mask（binary image）

     * 類別 1：道路（road）
     * 類別 0：非道路（non-road）

2. **評估分割效果**

   * 使用 Ground Truth（GT，人工標註結果）作為標準答案
   * 透過 **Mean Squared Error (MSE)** 作為主要評估指標
   * 分析預測結果與 GT 之間的誤差分佈

3. **降低運算成本**

   * 設計低時間複雜度的影像處理流程
   * 避免高成本運算（如大量 convolution 或深層迭代）

4. **嵌入式系統可行性**

   * 確保演算法可在資源受限平台上運行（如 MCU / edge device）
   * 評估：

     * 推論時間（inference time）
     * 記憶體使用量
   * 探討量化（quantization）或簡化計算的可能性

---

## 3. 流程

（待補）

---

## 4. 結果

（待補）

---

## 5. 優點

（待補）

---

## 6. 限制

（待補）

---

## 7. 結論

（待補）

