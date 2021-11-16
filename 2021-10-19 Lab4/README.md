## 練習一

### Description
（整數的和和平均數）請撰寫一個會將一連串整數相加並計算其平均數的程式。假定以所讀取的第一個整數，是用於指出接下來要輸入的數值的個數。

底下是一個輸入列的範例
```
7 678 234 315 489 536 456 367
```

### Input
無

### Output
平均數的小數點無條件捨去。

### Input Samples
```
7 678 234 315 489 536 456 367
```

### Output Samples
```
439
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
		
        Scanner s = new Scanner(System.in);
        int sum = 0, avg = 0;
        int num = s.nextInt();

        for (int i = 0 ; i < num ; i++) {
            int x = s.nextInt();
            sum = sum + x;
        }
        
        avg = sum / num;
        System.out.println(avg);
    }
}
```

## 練習二

### Description
（繪製長條圖）電腦的一項有趣的應用，便是用它來繪出統計圖表。

請撰寫一個程式讀入 5 個數（都在 1 到 30 之間），並依據所讀入之數的大小，印出一行相同數目的星號。

例如，如果程式讀到 7 的話，應會印出 `*******`。

### Input
無

### Output
無

### Input Samples
```
1 2 5 4 3
```

### Output Samples
```
*
**
*****
****
***
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void show(int n) {
        for (int j = 0 ; j < n ; j++) {
            System.out.print("*");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        for (int i = 0 ; i < 5 ; i++) {
            int num = s.nextInt();
            show(num);
        }
    }
}
```

## 練習三

### Description
（計算銷售額）某家網路零售商販售五種不同的產品，每一種產品的零售價如下表所示：

| 產品編號 | 零售價 |
| :-----: | :-----: |
| 1 | $2.98 |
| 2 | $4.50 |
| 3 | $9.98 |
| 4 | $4.49 |
| 5 | $6.87 |

請撰寫一個程式要求會計人員輸入如下的兩個數：（輸入 `-1 -1` 停止輸入）
- 產品編號
- 一天之內的銷售量

你的程式需要應用 `if … else if …` 敘述式來判斷每一項產品的零售價。此程式須計算並顯示上週賣出產品的總獲利。

### Input
無

### Output
四捨五入到小數點第二位

### Input Samples
```
1 3
2 5
3 3
4 2
5 3
-1 -1
```

### Output Samples
```
90.97
```

### Code
```java
import java.util.Scanner;
import java.lang.Math;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        double sell_price = 0;
        int no, sale;
        double sum = 0;
        
        do {
            no = s.nextInt();
            sale = s.nextInt();
            
            if(no == 1) {
            	sell_price = 2.98;
            }
            else if(no == 2) {
            	sell_price = 4.50;
            }
            else if(no == 3) {
            	sell_price = 9.98;
            }
            else if(no == 4) {
            	sell_price = 4.49;
            }
            else if(no == 5) {
            	sell_price = 6.87;
            }
            else {
            	sell_price = 0;
            }
            sum = sum + sell_price * sale;
        	
        } while(no != -1 && sale != -1);
        System.out.printf("%.2f", sum);
    }
}
```