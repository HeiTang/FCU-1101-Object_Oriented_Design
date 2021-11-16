## 練習一

### Description
（畢氏三元數）直角三角形的三邊可以都是整數。

構成直角三角形邊長的三個整數稱為畢氏三元數。這三個邊必須滿足以下公式：斜邊的平方等於另外兩邊的平方和。

尋找斜邊不大於 500 的所有畢氏三元數的 side1 和 side2。

使用一個三層的巢狀 for 迴圈來嘗試所有的可能性。這種計算方式就稱為「暴力法」。

許多人認為這不是一個好方法。但是從許多層面來看，這仍是很重要的技巧。

首先，電腦的威力以驚人的速度增加，幾年前的電腦需要好幾年或好幾世紀才能算出的問題，現在可能只花幾個小時、幾分鐘，甚至幾秒鐘之內就能算出來。

現今的微處理器晶片可以在一秒之內處理十億個指令。其次，在你將來的資訊科學課程中，你會發現還有許多有趣的問題沒有演算法可以解決，只能使用窮舉暴力法。

### Input
無

### Output
以一行的方式顯示畢氏三元數
```
%d %d %d\n
```
需過濾相同組合

### Input Samples
無

### Output Samples
```
3 4 5
5 12 13
6 8 10
7 24 25
```
（以下省略）

### Code
```java
public class Main {
    public static void main(String[] args) {
        for (int i = 3; i <= 500 ; i++) {
            for(int j = i + 1 ; j <= 500 ; j++) {
                for(int k = j + 1 ; k <= 500 ; k++) {
                    if(i * i + j * j == k * k){
                        System.out.printf("%d %d %d\n", i, j, k);
                    }
                }
            }
        }
    }
}
```

## 練習二

### Description
某家公司支付員工薪水的方式分為：
- 經理人員：領固定的週薪 $500。
- 時薪工：每週工作時數在 40 小時內，以「每小時工資 $8」計算，超過 40 小時的部分，則以「每小時工資的 1.5 倍」計算加班薪資。
- 抽佣金工：週薪為 $250 元加上當週銷售金額的 5.7%。
- 零工：按每週所生產的件數計酬──每位零工只能參與一種產品的生產，零工酬勞為商品單價的 50%，例如做一件 $4 元的商品可以拿到 $2 元。

請撰寫一個程式來計算每位員工的週薪，但你事先並不知道員工的人數。

每一類的員工都有他們自己的薪資代碼：1 代表經理人員、2 代表時薪工、3 代表抽佣金、4 代表零工。

請用 `switch` 根據每位員工的薪資代碼算出他們的薪資所得。

在 switch 裡提示使用者（薪資結算人員）輸入所需之員工工作資料，以根據員工的薪資代碼計算出薪資所得。

（注意：你可以在輸入的數值為 double 型別。）

### Input

#### **員工工作資料**
1. 首先輸入一個 `int` 代表有多少員工工作資料。
    ```
    6
    ```
2. 接下來輸入 `員工 ID`、`員工薪資代碼`、`工時`。
    - 當員工代碼為 4 代表零工時，格式如：`員工 ID`、`員工薪資代碼`、`生產件數`、`產品種類`。

    | 員工 ID | 員工薪資代碼 | 工時 / 生產件數 | 產品種類 |
    |:-------:|:------------:|:---------------:|:--------:|
    |A|1|45||
    |B|2|39||
    |C|2|44||
    |D|3|31||
    |E|4|200|Candy|
    |F|4|150|Chocolate|

#### **銷售金額**

1. 再來輸入一個 `int` 代表有多少商品銷售數量與商品單價。
    ```
    3
    ```
    | 商品名稱 | 銷售數量 | 商品單價 |
    |:-------:|:------:|:-------:|
    |Candy|300|3|
    |Chocolate|300|4|
    |Cake|300|5|

2. 當週銷售金額：所有商品銷售數量 * 商品單價的總和。
    - Ex: 300 x 3 + 300 x 4 + 300 x 5

### Output
列出所有員工的薪資。

抽佣金工（週薪為 $250 元加上當週銷售金額的 5.7%）: 請四捨五入到整數。

### Input Samples
```
6
A 1 45
B 2 39
C 2 44
D 3 31
E 4 200 Candy
F 4 150 Chocolate
3
Candy 300 3
Chocolate 300 4
Cake 300 5
```

### Output Samples
```
A 500
B 312
C 368
D 455
E 300
F 300
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        
        // 1 - 員工工作資料
        int staffNum = s.nextInt();                      // 員工數量
        int[] staffSalaryCode = new int[staffNum];       // 員工薪資代碼
        int[] staffWorkingHours = new int[staffNum];     // 員工工時/生產件數
        String[] staffId = new String[staffNum];         // 員工 ID
        String[] productCategory = new String[staffNum]; // 商品種類
        
        // 輸入員工資訊
        for(int i = 0 ; i < staffNum ; i++) {
            staffId[i] = s.next();
            staffSalaryCode[i] = s.nextInt();
            staffWorkingHours[i] = s.nextInt();
            if(staffSalaryCode[i] == 4) {
                productCategory[i] = s.next();
            }
        }
        
        // 2 - 銷售金額
        int productIncome = 0;                         // 商品收益
        int productNum = s.nextInt();                  // 商品數量
        int[] productSales = new int[productNum];      // 銷售數量
        int[] productUnitPrice = new int[productNum];  // 商品單價
        String[] productName = new String[productNum]; // 商品名稱
        
        // 輸入商品資訊
        for(int i = 0 ; i < productNum ; i++) {
            productName[i] = s.next();
            productSales[i] = s.nextInt();
            productUnitPrice[i] = s.nextInt();
        }

        // 計算總收益
        for(int i = 0 ; i < productNum ; i++) {
            productIncome += productSales[i] * productUnitPrice[i];
        }
        
        // 計算員工收益
        for(int i = 0 ; i < staffNum ; i++){
            double staffSalary = 0;
            switch(staffSalaryCode[i]) {
                case 1:
                    staffSalary = 500;
                    break;
                
                case 2:
                    if(staffWorkingHours[i] <= 40){
                        staffSalary = staffWorkingHours[i] * 8;
                    }
                    else {
                        staffSalary = 320;
                        staffSalary += (staffWorkingHours[i] - 40) * 12;
                    }
                    break;
                
                case 3:
                    staffSalary = productIncome * 0.057 + 250;
                    break;
                
                case 4:  
                    for(int j = 0; j < productNum; j++){
                        if(productCategory[i].equals(productName[j])){
                            staffSalary = staffWorkingHours[i] / 2 * productUnitPrice[j];
                        }
                    }
                    break;
            }
            System.out.printf("%s %.0f\n", staffId[i], staffSalary);
        }
    }
}
```

## 練習三

### Description
印出菱形

撰寫一個程式印出如下的菱形。

請盡量加大循環的次數（使用巢狀的 for 敘述式），並盡量減少輸出敘述式的數目。

### Input
無

### Output
無

### Input Samples 1
```
5
```

### Output Samples 1
```
    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *
```

### Input Samples 2
```
3
```

### Output Samples 2
```
  *
 ***
*****
 ***
  *
```

### Code
```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner s = new Scanner(System.in);
		int n = s.nextInt();
		for(int i = 0 ; i < n ; i++) {
			for(int j = n - 1 - i ; j > 0 ; j--) {
				System.out.print(" ");
			}
			for(int j = 0 ; j < (i + 1) * 2 - 1 ; j++) {
				System.out.print("*");
			}
            System.out.println();	
		}
		for(int i = 0 ; i < n - 1 ; i++) {
			for(int j = 0 ; j <= i ; j++) {
				System.out.print(" ");
			}
			for(int j = 0 ; j < (n - i - 1) * 2 - 1 ; j++) {
				System.out.print("*");
			}
            System.out.println();
		}
	}
}
```