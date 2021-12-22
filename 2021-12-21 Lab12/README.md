## 練習一

### Description
定義 `PowerFailureException` 例外類別，類別中應該有一個無參數的建構子。

如果在使用者所輸入的所需電量大於現有儲存電量，則抛出例外，`getMessage` 就會傳回 "Power Failure!"。

```
現有儲存電量為 3
輸入大於 3 時，抛出例外（throw exception）
```

注意: 沒使用 `Exception` 通過題目繳交者，將斟酌扣分。

請判斷輸入的資料再抛出例外，不要直接交範例程式碼，否則斟酌扣分。

### Input
第一個數字為接下來會輸入幾個 input。
接下來的數字為 input。

```
3         // 會輸入三個數字
1
2
3
```

### Output
如果大於 3 抛出例外（throw exception）。

### Input Samples
```
3
1
2
4
```

### Output Samples
```
Power Failure!
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int count = s.nextInt();
        int powerOwn = 3;

        try {
            for (int i = 0; i < count; i++) {
                int powerNeed = s.nextInt();
                if (powerNeed > powerOwn) {
                    throw new PowerFailureException();
                }
            }

        } catch (PowerFailureException ex) {
            System.out.println(ex.getMessage());
        }
    }

}

class PowerFailureException extends Exception {
    public String getMessage() {
        return ("Power Failure!");
    }
}
```

## 練習二

### Description
在設定密碼時，如果密碼的位數為每個位數的值都是相同的，如 1111，這是不安全的密碼，稱為 bad number。

請定義帶有 `int` 類型訊息的例外類別 `BadNumberException`。

請定義一個帶有整數引數的建構子，將所傳入的整數值設定為 badNumber，其初使化的訊息字串為 "BadNumberException" + badNumber。

另外，再定義沒有引數的建構子，其中在沒有引數的建構中，初使化的訊息字串為 "BadNumberException"。

當使用者輸入的密碼為 0000、1111、...、9999，帶有整數引數的建構子抛出例外，如果使用者輸入的密碼為負數，則由沒有引數的建構子抛出例外。

### Input
無

### Output
無

### Input Samples 1
```
1111
```

### Output Samples 1
```
BadNumberException 1111
```

### Input Samples 2
```
-1
```

### Output Samples 2
```
BadNumberException
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int passwd = s.nextInt();

        String passwd_str = String.valueOf(passwd);
        char[] passwd_arr = passwd_str.toCharArray();
        boolean badNum = true;

        for (int i = 0; i < passwd_str.length() - 1; i++) {
            if (passwd_arr[i] != passwd_arr[i + 1]) {
                badNum = false;
            }
        }

        try {
            if (badNum == true && passwd >= 0) {
                throw new BadNumberException(passwd);
            } else if (passwd < 0) {
                throw new BadNumberException();
            }

        } catch (BadNumberException ex) {
            System.out.println(ex.getMessage());
        }
    }

}

class BadNumberException extends Exception {

    int Badnumber;
    String msg = "";

    public BadNumberException(int Badnumber) {
        this.Badnumber = Badnumber;
        this.msg = "BadNumberException " + this.Badnumber;
    }

    public BadNumberException() {
        this.msg = "BadNumberException";
    }

    public String getMessage() {
        return (msg);
    }
}
```

## 練習三

### Description
呈第二題，定義輸入負數的例外類別 `NegativeNumberException`，並使用 catch(NegativeNumberException e)，並輸出 "NegativeNumber"。

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
NegativeNumberException -1
```

### Input Samples 2
```
1111
```

### Output Samples 2
```
BadNumberException 1111
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int passwd = s.nextInt();

        String passwd_str = String.valueOf(passwd);
        char[] passwd_arr = passwd_str.toCharArray();
        boolean badNum = true;

        for (int i = 0; i < passwd_str.length() - 1; i++) {
            if (passwd_arr[i] != passwd_arr[i + 1]) {
                badNum = false;
            }
        }

        try {
            if (badNum == true && passwd >= 0) {
                throw new BadNumberException();
            } else if (passwd < 0) {
                throw new NegativeNumberException();
            }
        } catch (BadNumberException be) {
            System.out.printf("%s %d", be.getMessage(), passwd);
        } catch (NegativeNumberException ne) {
            System.out.printf("%s %d", ne.getMessage(), passwd);
        }
    }

}

class BadNumberException extends Exception {

    int Badnumber;
    String msg = "";

    public BadNumberException() {
        this.msg = "BadNumberException";
    }

    public String getMessage() {
        return (msg);
    }
}

class NegativeNumberException extends Exception {

    int Negativenumber;
    String msg = "";

    public NegativeNumberException() {
        this.msg = "NegativeNumberException";
    }

    public String getMessage() {
        return (msg);
    }
}
```
