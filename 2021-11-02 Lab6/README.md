## 練習一

### Description
試寫一程式，可多次輸入月份，然後在類別中定一個方法用來判斷所輸入所屬的季節。

(3 ~ 5 月為春季、6 ~ 8 月為夏季、9 ~ 11 月為秋季、12 ~ 2 月為冬季)。

-1 代表停止輸入。

### Input
無

### Output
無

### Input Samples
```
1
4
7
10
-1
```

### Output Samples
```
winter
spring
summer
fall
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int i = 0;
        while(i != -1) {
            i = s.nextInt();
            System.out.printf("%s\n", getSeason(i));
        }
    }
	
    public static String getSeason(int month) {
        String season = "";
        switch(month) {
            case 12:
            case 1:
            case 2:
                season = "winter";
                break;
            case 3:
            case 4:
            case 5:
                season = "spring";
                break;
            case 6:
            case 7:
            case 8:
                season = "summer";
                break;
            case 9:
            case 10:
            case 11:
                season = "fall";
                break;
        }
        return season;
    }
}
```

## 練習二

### Description
試寫一個程式，可由鍵盤讀入一個 4 位數的整數，代表西洋的年份，然後在類別中定一個方法用來判別這個年份是否為閏年。

每四年一閏，每百年不閏，每四千年不閏，例如:西元 1900 年為 4 的倍數，但可被 100 整除，所以不是閏年。

同理，2000 年為閏年，因為可被 400 整數除。

### Input
一個整數，代表年份。

有多筆輸入，-1 代表停止。

### Output
無

### Input Samples
```
1900
1999
2000
2004
-1
```

### Output Samples
```
No
No
Yes
Yes
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int year;
        while(true) {
            year = s.nextInt();  
            if(year == -1) {
                break;
            }
            System.out.printf("%s\n", judgeLeapYear(year));
        }
    }

    public static String judgeLeapYear(int year) {
        if( year %4 == 0 && year % 100 != 0 || year % 400 == 0) {
            return "Yes";
        }
        else {
            return "No";
        }
    }
}
```

## 練習三

### Description
試寫一個程式，可由鍵盤讀入兩個整數，然後在類別中定一個方法計算兩個正整數的最大公因數。

### Input
無

### Output
無

### Input Samples
```
34 10
20 30
72 96
4923 513
-1 -1
```

### Output Samples
```
2
10
24
9
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int num1, num2;
        while(true) {
            num1 = s.nextInt();  
            num2 = s.nextInt();  
            if(num1 == -1 && num2 == -1) {
                break;
            }
            System.out.println(getGCD(num1, num2));
        }
    }

    public static int getGCD(int num1, int num2) {
        for(int i = num1; i > 0; i--) {
            if(num1 % i == 0) {
                if(num2 % i == 0){
                    return i;
                }
            }
        }
        return 1;
    }
}
```