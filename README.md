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



