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

(1) 先把原圖轉成 HSV <br>
(2) 把影像切成很多小區塊 <br>
(3) 每個小區塊統計：
* H histogram
* S histogram
* V histogram

(4) 把這三個 histogram 當成該 block 的特徵 <br>
(5) 用 clustering 把特徵相似的 block 分成同一類 <br> 
(6) 最後把每一類上不同顏色，形成 segmentation 結果 <br>

---

## 4. 結果



---

## 5. 優點

(1) 無需訓練（unsupervised）
(2) 可解釋性高
(3) 對亮度變化較穩定
(4) 抗雜訊（block-based）
(5) 特徵可擴充（HSV / LBP 等）
(6) 可控制 segmentation 粗細
(7) 計算簡單，適合硬體實作

---

## 6. 限制

(1) 忽略空間與結構資訊，判斷純靠顏色分布特徵
(2) 無法描述紋理
(3) segmentation 結果有方塊感
(4) 對參數敏感
(5) KL divergence 非對稱
(6) clustering 易陷入局部最佳
(7) 無語意理解能力
(8) 對道路 segmentation 容易混淆（灰色物體）

---

## 7. 結論

目前此版本過度依賴顏色分布，雖然部分影像中的柏油路具有顏色上的特徵，但不確定性仍然較高，若能夠加上其他 histogram 特徵並與 HSV histogram 一起做 clustering ，或許能做到更準確且全面的判斷。

