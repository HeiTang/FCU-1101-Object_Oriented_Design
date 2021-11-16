## 題目一 - 計算圓面積

### Description
使用者在 console 輸入 integer 與 String，並在 console 印出結果。

請計算圓面積（`半徑*半徑*3.1415926`）

### Input
輸入為一個 int 代表圓的半徑以及一個 String 代表人名（格式請參考範例）。


### Output
輸出程式提示與結果（格式請參考範例）。

### Input Samples 1
```
3
Sammy
```

### Output Samples 1
```
Enter a integer:
Enter a you name:
Hi Sammy, The area of a circle with a radius of 3 is 28.274333
```

### Input Samples 2
```
20
Ian
```

### Output Samples 2
```
Enter a integer:
Enter a you name:
Hi Ian, The area of a circle with a radius of 20 is 1256.637040
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.println("Enter a integer:");
        int integer = s.nextInt();

        System.out.println("Enter a you name:");
        String name = s.next();

        double circleArea = integer * integer * 3.1415926;
        System.out.printf("Hi %s, The area of a circle with a radius of %d is %.6f", name, integer, circleArea);
    }
}
```

## 題目二 - 日期與時間

### Description
UNIX 時間，或稱 POSIX 時間是 UNIX 或類 UNIX 系統使用的時間表示方式：從 UTC 1970 年 1 月 1 日 0 時 0 分 0 秒起至現在的總秒數。

題目將輸入一個 UNIX 時間請把它轉換成日期。

例如 2021/11/16 16:00:00（GMT+8 台灣時間），這個時間點的 UNIX 時間為 1637049600（秒）。

輸出日期的格式為 `Instant`，表示的是時間線上的一個點，也就是時刻，可以和 `Date` 做一個比較。

比較直接的一個不同就是 `Instant` 獲取的是 UTC 的時間，而 `Date` 是根據當前伺服器所處的環境的預設時區來獲取的當前時間。

- Instant 格式的範例如下:
    
    ```
    2021-11-16T08:00:00Z  = Unix Time 1637049600（秒）
    ```

- 提示：

    - 您可以從 1970 年 1 月 1 日，慢慢算到 2021 年，但是 Java 提供了 `Data` 物件讓你輕鬆轉換它。

    ```java
    long unixTime = 1637049600000L; // 單位是毫秒
    Date date = new Date(unixTime);
    System.out.println(date.toInstant());
    ```
    print 結果：
    ```
    2021-11-16T08:00:00Z
    ```

### Input
UNIX 時間單位是**毫秒**

### Output
輸出為日期，格式為 Instant

例如：
```
2021-11-16T08:00:00Z
```

### Input Samples
```
1637049600000
```

### Output Samples
```
2021-11-16T08:00:00Z
```

### Code
```java
import java.util.*;
import java.text.*;
import java.time.*;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        long UNIX_Time = s.nextLong();	
        Date UTC_Time = new Date(UNIX_Time);
        System.out.print(UTC_Time.toInstant());
    }
}
```

## 題目三 - 入校pass

### Description
請建立一個學生類別（其中所需定義的資料項包括姓名、學號、體溫，如有多餘考量，可自行定義）。

請定義設定姓名、學號、體溫的方法，還要有一個顯示學生資料的方法。

請定義一個判斷能否入校的方法（體溫 > 38 不能入校）。

### Input
- 輸入 1：表示新增學生，下一行會有姓名、學號、體溫。

    ```
    Leo D0915357 36.5
    ```
    > 示意

- 輸入 2：請顯示學生資料（顯示結果在 Output Description）。

    ```
    Leo
    ```
    > 示意

- 輸入 3：請判斷能否進入校園。

    ```
    Leo
    ```
    > 示意

- 輸入 -1：表示程式結束。

### Output
- 輸入 2：請顯示學生資料
    - 顯示所有學生資料時請顯示以下格式：   

        | 姓名 | 學號 | 體溫 |
        |:--------:|:--------:|:----:|
        |  Leo  |  D0915357   | 36.5  |
        > 示意

- 輸入 3：請顯示學生是否能入校。
    - 姓名是否能入校。
    - 顯示所有能否入校時請顯示以下格式：

        ```
        Leo pass
        ```

### Input Samples
```
1
Leo D0915357 36.5
1
Amy D0995175 38.3
2
Leo
3
Leo
3
Amy
-1
```

### Output Samples
```
Leo D0915357 36.5
Leo pass
Amy fail
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        Student[] stu = new Student[10];
        int index = 0, func = 0;

        while(func != -1) {
            func = s.nextInt();
            
            if(func == 1) {
                stu[index] = new Student();
                stu[index].Name = s.next();
                stu[index].StudentId = s.next();
                stu[index].Degrees = s.nextFloat();
                index++;
            }
            
            if(func == 2) {
                String name = s.next();
                for(int i = 0 ; i < index ; i++) {
                    if(stu[i].Name.equals(name)) {
                        System.out.printf("%s %s %s\n", stu[i].Name, stu[i].StudentId, stu[i].Degrees);
                        break;
                    }
                }
            }
            
            if(func == 3) {
                String name = s.next();
                for(int i = 0 ; i < index ; i++) {
                    if(stu[i].Name.equals(name)) {
                        if(stu[i].Degrees > 38) {
                            System.out.printf("%s fail\n", stu[i].Name);
                        } else {
                            System.out.printf("%s pass\n", stu[i].Name);
                        }
                        break;
                    }
                }
            }
        }
    }
}

class Student{
    public String Name;
    public String StudentId;
    public float Degrees;
}
```

## 題目四 - 季節

### Description
試寫一程式，可多次輸入月份，請建立一個月份類別，其中定義月份與季節。

然後在類別中定義一個方法用來判斷所輸入所屬的季節，並且輸出季節。

注意請務必使用類別（class）來完成此題目

### Input
3 ~ 5 月為春季、6 ~ 8 月為夏季、9 ~ 11 月為秋季、 12 ~ 2 月為冬季。
`-1` 代表停止輸入。

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
        Season[] sea = new Season[100];
        int month = 0, index = 0;

        while(month != -1) {
            month = s.nextInt();
            sea[index] = new Season(month);
            sea[index].getSeason();
            index++;
        }
    }
}

class Season {
    private String Season;
    private int Month;

    public Season(int month) {
        this.Month = month;
    }

    public void getSeason() {
        switch(this.Month) {
            case 12:
            case 1:
            case 2:
                this.Season = "winter";
                break;
            case 3:
            case 4:
            case 5:
                this.Season = "spring";
                break;
            case 6:
            case 7:
            case 8:
                this.Season = "summer";
                break;
            case 9:
            case 10:
            case 11:
                this.Season = "fall";
                break;
            case -1:
                this.Season = "";
                break;
        }
        System.out.printf("%s\n", this.Season);
    }
}
```