## Dataset

網址：https://www.vision.caltech.edu/datasets/cub_200_2011/

介紹：
Caltech-UCSD Birds-200-2011 (CUB-200-2011) 是一個鳥類圖像辨識資料集，其中包含 200 種不同種類的鳥類，共有11,788 張圖像。每一張圖像都有一個對應的標籤，表示這張圖像所代表的鳥的種類。
CUB-200-2011 的圖像分辨率不同，大小範圍從 224x224 到 600x600 不等。

## Transfer Learning流程
- Method 1

  1. 將利用CUB-200-2011資料集預先訓練好的模型讀進來。
  2. frozen -- 凍結預先訓練好的模型的權重，使其在訓練中不會被更新：將預先訓練好的模型的權重設為False(不可訓練)，以保留模型在大型資料集上學到的通用特徵，避免出現overfitting 。
  3. new layer -- 在預先訓練好的模型的頂部添加一個新的全連接層，用來將模型的輸出與鳥類圖像的標籤進行匹配，然後使用鳥類圖像的數據集來訓練新的全連接層。
- Method 2

  1. 選擇一個預先訓練好的模型：resnet152。
  2. frozen -- 凍結預先訓練好的模型的權重，使其在訓練中不會被更新：將預先訓練好的模型的權重設為False(不可訓練)，以保留模型在大型資料集上學到的通用特徵，避免出現overfitting。
  3. new layer -- 在預先訓練好的模型的頂部添加一個新的全連接層，用來將模型的輸出與鳥類圖像的標籤進行匹配，然後使用鳥類圖像的數據集來訓練新的全連接層。

## 模型表現
- Method 1

  ![image](https://github.com/yy1200/Bird-Classification-using-Transfer-Learning/assets/92247082/ef59bd2f-a931-48c0-a6f0-5ea15a63e05d)
- Method 2
  
  ![image](https://github.com/yy1200/Bird-Classification-using-Transfer-Learning/assets/92247082/90c69601-1bdf-455a-93ea-61f80861c76b)

## Conclusion
- Method 1 (用CUB-200-2011建模)

  選擇CUB-200-2011作為source task及data，並用transfer learning在小型鳥類圖像數據集上實現了47%的準確率
- Method 1 (resnet152)

  選擇已經在大型數據集上pretrain好的模型進行transfer learning，並在小型鳥類圖像數據集上實現了92%的準確率。

本次實驗表明了在單用鳥類圖像，且數據集並不龐大的情況下，預測準確率並不高，能學到的特徵有限，還需要對數據或模型做更多處理來提高分類成效，而選擇合適的pretrain好的模型能利用transfer learning快速適應新的任務，達到較高的準確率。




