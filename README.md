# Two-Stage-CMOS-OP-AMP

![螢幕快照 2022-08-30 10-33-55](https://user-images.githubusercontent.com/68816726/187335773-a144c000-54c1-497d-8463-13d7ed5b4ac4.png)

## DC voltage Gain:
由小訊號模型計算此OP之Gain：

![IMG_0020](https://user-images.githubusercontent.com/68816726/187338105-1d9a2b62-9ebd-4ce1-aa35-63eb6d2ae857.png)

因為Gain = Vo/Vin，由左邊的相依電流源乘上右邊的電阻為Vo，再除Vi 即為此OP第一級的Gain

![IMG_0017](https://user-images.githubusercontent.com/68816726/187337916-ec489ab3-0dc6-4c7b-8ab5-40a3f902a43b.png)

同理可推出第二級的Gain:

![IMG_0018](https://user-images.githubusercontent.com/68816726/187339473-0a21e976-5e3a-4a05-877b-cefbf54caf18.png)

由此可知整個放大器的Gain

![IMG_0019](https://user-images.githubusercontent.com/68816726/187339683-92b241e6-8347-4097-b261-88213a71339c.png)

## 頻率響應：

定義：
對一個線性非時變系統，以不同頻率之正弦波信號輸入系統，探討輸出與輸
入之間的振幅增益與相位變化的響應關係，稱為頻率響應。



小訊號模型中，用節點電壓法列出兩式

![IMG_0022](https://user-images.githubusercontent.com/68816726/187341788-04704c69-fe47-46f0-a012-b31ac3c34991.png)

整理可得

![圖片](https://user-images.githubusercontent.com/68816726/187342481-2b78c1f2-92d4-436a-9664-c4453060e5d4.png)

### 求Zero(讓分子多項式為0):

![圖片](https://user-images.githubusercontent.com/68816726/187344391-ec82d6e8-cd7e-4bfb-a629-eb24b67029d3.png)

### 求pole(讓分母多項式為0):
分母的多項式可以寫成，分為s的一次項與二次項：

![圖片](https://user-images.githubusercontent.com/68816726/187345019-5b37678d-8b1d-4d42-a3ef-51540ffa9220.png)

先解第一個pole

與上式比較可以列出
![圖片](https://user-images.githubusercontent.com/68816726/187345258-124e2dd7-46bc-4c08-b405-aeae8bb72454.png)

最後因為C1通常比Cc小很多所以可以省略

第二個pole

![圖片](https://user-images.githubusercontent.com/68816726/187345819-0904c95e-6fc5-4272-b056-13c503acfb37.png)


### phase margin:

定義:波德圖的增益曲線為 0dB 時，所對應的角度與-180度的相差角度稱為 phase margin

## Design of two stage op amp:


![螢幕快照 2022-08-30 23-11-20](https://user-images.githubusercontent.com/68816726/187474323-ba4f0803-64c6-4da5-abcc-8488309f9fd7.png)

### Design Principle:

* 因為λ的關係，建議使用 L > 2Lmin ，所以用 L = 1u
* 為了提昇OP的效能，我們會調整L的大小，但 W/L 保持不變 

![圖片](https://user-images.githubusercontent.com/68816726/187581493-4089bcc0-a24e-4784-a60d-1db4d977677a.png)

![圖片](https://user-images.githubusercontent.com/68816726/187581526-9d298f85-337e-447d-baf7-1804cd24fce0.png)

* 接著計算補償電容與電阻的大小
* 先設計第一級再設計第二級

  1. 補償電容 ： 
  * 為了滿足 Cc > 0.22CL ，（CL = 1pF），所以 Cc 必須大於 220fF
  * slew rate 須達到 10V /|mus ，Cc 需為 10pf
  * 為達到上述兩個要求，我們選擇 Cc = 3pf 


  2. 設計M4、M7 ：
  * gm1 = GBW × Cc × 2π ， GBW 就是 unity gain frequency （增益為1時的頻率）
  * GBW 設計目標為 100MHZ
  * gm1 = 100M HZ × 5pF × 2π = 302µ ， 為了方便我們取 510u 
  
  ![圖片](https://user-images.githubusercontent.com/68816726/187583432-a7398b3f-e65b-469e-b7a0-3cc803d35c4f.png)
  
  ![圖片](https://user-images.githubusercontent.com/68816726/187583731-45965395-395b-4cdc-b03a-a6d4a5edb398.png)
  * 最後，取 20 當作設計結果
  
  
  3. 設計M5、M6 ：
  * 為了達到輸出範圍大於800mV　，　至少需要　800mV　的共模輸入範圍在零點之前　（ｇａｉｎ　為１處）
  
  ![圖片](https://user-images.githubusercontent.com/68816726/187585193-65c4c939-9528-4714-8b84-32500667212b.png)

　４. 設計M2、M3 ：
  * 取適當的ICMR(-)以決定M5的大小
  ![圖片](https://user-images.githubusercontent.com/68816726/187585942-26c4de46-a687-42d7-9853-f45a115abd57.png)
  
  5. 設計M8 ：
  * 0.22gm2 > gm1 ， 所以 gm2 > 2318µ 
  * VDS5 = VDS6 = VDS8 ， VGS5 = VGS6 = VGS8
  ![圖片](https://user-images.githubusercontent.com/68816726/187586743-0559c54b-0148-4a4b-a8c0-5e3a06d2b850.png)
  
  6. 設計M9 ：
  
  ![圖片](https://user-images.githubusercontent.com/68816726/187587172-60e57228-f5a2-4d89-9de9-8878872974f5.png)
  
  7. 設計 Rz ：
  * Rz = 1/gm2 = 5k
  
  8.共模、差模增益 ： 
  * 檢查gain ， 調整計算出的參數以達到要求
  
  
  

