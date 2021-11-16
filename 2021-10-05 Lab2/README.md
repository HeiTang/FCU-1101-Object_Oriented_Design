## 練習一

### Description
遊樂場的電子遊戲機根據結果輸出禮卷。可以用 10 張禮卷兌換一個糖果，也可以用 3 張禮卷兌換一塊口香糖。
請寫一個程式，定義一個變數並初始化為 108 張，接下來程式輸出能夠得到多少糖果棒與口香糖（假設先將全部禮卷用於糖果棒，然後剩餘的禮卷兌換口香糖）。

### Input
無

### Output
輸出
```
10 2
```

### Input Samples
無

### Output Samples
```
10 2
```

### Code
```java
public class Main{ 
    public static void main(String[] args){
        System.out.printf("%d %d", 108 / 10, 108 % 10 / 3);
    }
}
```

## 練習二

### Description
撰寫一個程式計算單利（simple interest），當借用的本金（principal amount）為 1000，利率（interest rate）為 5%，借用的年數（number of years）為 5 年。請使用適當的資料型態宣告這些變數。

請使用下列公式計算單利：
```
simple interest = (principal amount * interest rate * number ofyears)/100
```
輸出：250.00

### Input
無

### Output
輸出
```
250.00
```

### Input Samples
無

### Output Samples
```
250.00
```

### Code
```java
public class Main{
    public static void main(String[] args){
        int principal_amount = 1000;
        int number_ofyears = 5;
        float interest_rate = 5;
        float simple_interest = (principal_amount * interest_rate * number_ofyears) / 100;
        System.out.printf("%.2f", simple_interest);
    }
}
```