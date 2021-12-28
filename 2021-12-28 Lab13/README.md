## 練習一

### Description
請在 Java 程式的 `main()` 方法建立例外處理程式（try catch）敘述處理 `IllegalArgumentException` 例外，

這個例外是由 `cal()` 方法所丟出，由 `main()` 方法接手處理。

上述方法 `cal()` 需要傳入 3 個參數計算 a * b / c 的值，如果 c 為 0 時，則抛出例外，而例外說明為"c不能是0"。

### Input
輸入三個數字 a b c

### Output
如果輸入的 c 為 0，則拋出 excrption。
如果輸入的 c 不為 0，則顯示 a * b / c。

### Input Samples 1
```
1 3 0
```

### Output Samples 1
```
c不能是0
```

### Input Samples 2
```
3 3 3
```

### Output Samples 2
```
3
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) throws IllegalArgumentException {

        Scanner s = new Scanner(System.in);
        int a = s.nextInt();
        int b = s.nextInt();
        int c = s.nextInt();

        try {
            col(a, b, c);
        } catch (IllegalArgumentException e) {
            System.out.println(e.getMessage());
        }

    }

    public static void col(int a, int b, int c) throws IllegalArgumentException {
        if (c == 0) {
            throw new IllegalArgumentException();
        } else {
            System.out.println(a * b / c);
        }
    }

}

class IllegalArgumentException extends Exception {
    String msg;

    public IllegalArgumentException() {
        msg = "c不能是0";
    }

    public String getMessage() {
        return (msg);
    }
}
```

## 練習二

### Description
請建立 `printNum()` 方法顯示 2n+1 的數例，例如：1、3、5、7…，

其參數是整數 int 且抛出下列例外物件：

- IllegalArgumentException：當參數小於 0

- ArithmeticException：當參數大於 100
### Input
無

### Output
無

### Input Samples 1
```
-1
```

### Output Samples 1
```
Argument should be larger than 0
```

### Input Samples 2
```
101
```

### Output Samples 2
```
Argument should be smaller than 100
```

### Input Samples 3
```
5
```

### Output Samples 3
```
1,3,5,7,9,
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner s = new Scanner(System.in);
        int times = s.nextInt();

        try {
            printNum(times);
        } catch (Exception e) {
            System.out.print(e.getMessage());
        }
    }

    public static void printNum(int times) throws IllegalArgumentException, ArithmeticException {
        if (times <= 0) {
            throw new IllegalArgumentException();
        } else if (times >= 100) {
            throw new ArithmeticException();
        } else {
            for (int i = 0; i < times; i++) {
                System.out.printf("%d,", 2 * i + 1);
            }
        }
    }

}

class IllegalArgumentException extends Exception {
    String msg = "Argument should be larger than 0";

    public String getMessage() {
        return msg;
    }
}

class ArithmeticException extends Exception {
    String msg = "Argument should be smaller than 100";

    public String getMessage() {
        return msg;
    }
}
```

## 練習三

### Description
請建立 `ArguementException` 自訂例外類別，類別可以處理參數傳入字串的例外。

如果參數字串內含空白字元或英文字母，在轉換成整數 int 時會產生錯誤。

請依錯誤代碼 1（空白字元）、2（英文字母）、3（符號）顯示不同的錯誤訊息。

### Input
無

### Output
無

### Input Samples 1
```
1 1
```

### Output Samples 1
```
ArguementException:1 空白字串
```

### Input Samples 2
```
1Abc233
```

### Output Samples 2
```
ArguementException:2 英文字母
```

### Input Samples 3
```
1%@1
```

### Output Samples 3
```
ArguementException:3 符號
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) throws ArguementException {

        Scanner s = new Scanner(System.in);
        String msg;

        try {
            String str = s.nextLine();
            for (int i = 0; i < str.length(); i++) {
                char oneWord = str.charAt(i);
                if (oneWord < 48 || oneWord > 57) {
                    if (oneWord == 32) {
                        msg = "空白字串";
                        throw new ArguementException(1, msg);
                    } else if ((40 < oneWord && oneWord < 91) || (96 < oneWord && oneWord < 123)) {
                        msg = "英文字母";
                        throw new ArguementException(2, msg);
                    } else {
                        msg = "符號";
                        throw new ArguementException(3, msg);
                    }
                }
            }

        } catch (Exception e) {
            System.out.print("ArguementException:" + e.getMessage());
        }
    }
}

class ArguementException extends Exception {
    private String msg;

    public ArguementException(int num, String msg) {
        this.msg = num + " " + msg;
    }

    public String getMessage() {
        return (this.msg);
    }
}
```
