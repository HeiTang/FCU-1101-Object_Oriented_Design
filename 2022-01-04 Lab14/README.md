## 練習一

### Description
費伯那契數列

```
0, 1, 1, 2, 3, 5, 8, 13, 21, …
```

以 0 和 1 起頭，然後接下來的每一項均為其前兩項的和。

1. 撰寫一個非遞迴的函式 `fibonacci(n)`，計算第 n 個 Fibonacci 數。
   - 以 unsigned int 為函數的參數，並以 unsigned long longint 為傳回值資料型別。

2. 撰寫一個遞迴的函式。

請使用遞迴完成題目，否則斟酌給分。

### Input
無

### Output
請根據輸入的第 ? 項，輸出對應的費伯那契數。
項目:0 1 2 3 4 5 6 7......
數列:0 1 1 2 3 5 8 13.........

### Input Samples 1
```
3
```

### Output Samples 1
```
2
```

### Input Samples 2
```
9
```

### Output Samples 2
```
34
```

### Input Samples 3
```
13
```

### Output Samples 3
```
233
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner s = new Scanner(System.in);
        int num = s.nextInt();
        System.out.println(fibonacci(num));
    }

    public static int fibonacci(int num) {
        if (num == 0 || num == 1)
            return num;
        return fibonacci(num - 1) + fibonacci(num - 2);
    }
}
```

## 練習二

### Description
（遞迴質數）請寫一個遞迴函式 `isPrime`，判斷給定的輸入值是否為質數。

請在程式中使用此函式。

hint:通過將其除以 n 以下的所有數字。

ex:假設輸入是 7，以遞迴方式從 6 開始除到 1，如果這中間都沒有數字能整除它，那就代表 7 是質數。

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
isPrime
```

### Input Samples 2
```
509
```

### Output Samples 2
```
isPrime
```

### Input Samples 3
```
8
```

### Output Samples 3
```
notPrime
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner s = new Scanner(System.in);
        int num = s.nextInt();

        if (isPrime(num, 2)) {
            System.out.println("notPrime");
        } else {
            System.out.println("isPrime");
        }
    }

    public static boolean isPrime(int num, int index) {
        if (num <= 2)
            return (num == 2) ? false : true ;
        if (num % index == 0)
            return true ;
        if (num < index * index)
            return false;
        return isPrime(num, index + 1);
    }
}
```
