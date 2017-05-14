
# [HOWTO]如何挑選演算法及上傳

## Summary 
知道有哪些管道可以找到參考的演算法,會卡觀的狀況及如何上傳。

## 題目介紹:
Ebay-Kleinanzeigeng 二手車的價格資料，其中包含車價、車型、品牌、車齡、配件、週轉日數等資訊，試圖從這些變數中預測二手車價。
我們從二手車價資料中整理出 2 萬筆資料，以 5000 筆為 trainset，包含車價資訊，另外 5000 筆為 testset，沒有車價資訊

[訓練資料集、測試資料集、詳細比賽說明](https://dc.dsp.im/main/content/used-car-price-challenge)    

## 如何挑選演算法  
身為一個生手，學習別人成功使用的演算法是上手方法之一。  
在cortanaintelligence輸入 "Price"
你可以找到這一篇 [Quantile Regression: Car price prediction](https://gallery.cortanaintelligence.com/Experiment/536a12847d94444c86ed231b96d97863)  
點選"Open in Studio"
價格看起來是有區間分布

## 如何將比賽資料集套入  
### 直覺式  
將原本 "Automobile price data (Raw)"的資料移除，把比賽的trainset放上去。  
結果...會炸在"Tune Model Hyperparameters" 因為比賽的資料有五千筆，我嘗試硬跑跑了兩個小時還是跑不出來。

### Partition and Sample 
 "Partition and Sample" Module",將資料縮減成五百多筆。
 [Partition and Sample" Module](https://www.evernote.com/shard/s220/sh/5b52130f-be4b-4377-89ea-45b433582ac2/e555306dad676e5371cf957fbba9be8f)
把"Stratified split for sampling"選成True.我在看文件的時候，看起來這可以按比例去Sampling,我下階段要研究它Sampling的方式,看是否能優化結果。

## 如何上傳 
按下"Setup Predictive Experience"  
將testset上傳,按照下面的畫面接
[Upload](https://www.evernote.com/shard/s220/sh/070334c7-8f92-4086-9d44-5397c80f0a82/fa6d400a90c503322f4cd6bdcb1c07dd)
在SelectColumn選取你要選的欄位。
ConverToCsv的地方按右鍵下載
記得下載後第二個row欄位要改成Predict,才能上傳。

## Next  
出來準度是0分不是很意外XD  
主要是我卡在一些小地方卡很久,我決定先把如何上傳這件事情搞定。
所以,很多選項我都是用懶人預設,預測價格我應該也要用 Quantile的方式來選擇價格
我下一階段會用Quantile 選擇價格,review Sampling的方法
看看準度是否能增加
