## 練習一

### Description
使用者在 console 輸入 integer、float 與 String，並在 console 印出結果。

### Input
無

### Output
輸出程式提示與結果(格式請參考範例)
> hint:科學記號能用 `System.out.printf("%.2e", ans);`

### Input Samples 1
```
120
3.14159
Amy
```

### Output Samples 1
```
Enter a integer:
Enter a float point number:
Enter a you name:
Hi Amy, the multiplication of 120 and 3.14159 is 3.77e+02
```

### Input Samples 2
```
11
51.51
Jim
```

### Output Samples 2
```
Enter a integer:
Enter a float point number:
Enter a you name:
Hi Jim, the multiplication of 11 and 51.51 is 5.67e+02
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
      
        System.out.println("Enter a integer:");
        int integer = s.nextInt();
		
        System.out.println("Enter a float point number:");
        float number = s.nextFloat();
		
        System.out.println("Enter a you name:");
        String name = s.next();

        System.out.printf("Hi %s, the multiplication of %d and " + number + " is %.2e",name , integer, integer * number);
    }
}
```

## 練習二

### Description
奇數與偶數判斷

### Input
無

### Output
無

### Input Samples 1
```
120
```

### Output Samples 1
```
The input integer is Even Number
```

### Input Samples 2
```
5
```

### Output Samples 2
```
The input integer is Odd Number
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int integer = s.nextInt();
        if (integer % 2 == 0) {
            System.out.print("The input integer is Even Number");
        }
        else {
            System.out.print("The input integer is Odd Number");
        }
    }
}
```

## 練習三

### Description
- 使用者可在 console 輸入二個字串 String。
- 比較二字串是否一樣（忽略大小寫），並在 console 印出結果。

### Input
無

### Output
無

### Input Samples 1
```
Abc
aBc
```

### Output Samples 1
```
Enter a string 1:
Enter a string 2:
The two strings are the same
```

### Input Samples 2
```
Abc
xyz
```

### Output Samples 2
```
Enter a string 1:
Enter a string 2:
The two strings are not the same
```

### Code
```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        
        System.out.println("Enter a string 1:");
        String s1 = s.next();
        
        System.out.println("Enter a string 2:");
        String s2 = s.next();
        
        if (s1.equalsIgnoreCase(s2)) {
            System.out.println("The two strings are the same");
        }
        else {
            System.out.println("The two strings are not the same");
        }
    }
}
```

## 練習四

### Description
- 使用者可在 Console 輸入 Integer。
- 如果輸入的 Integer 介於 1 ~ 9 之間，則在 Console 印出相對應的英文，否則印出 `OTHER`。

### Input
無

### Output
數字英文轉換參考：
```
ONE
TWO
THREE
FOUR
FIVE
SIX
SEVEN
EIGHT
NINE
```
（輸出不需要加 `"` 號）

### Input Samples 1
```
1
```

### Output Samples 1
```
Enter a integer:
The input integer is ONE
```

### Input Samples 2
```
20
```

### Output Samples 2
```
Enter a integer:
The input integer is OTHER
```

### Code
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.println("Enter a integer:");
        int num = s.nextInt();
        String str; 
        
        switch(num) {
            case 1: str = "ONE"; break;
            case 2: str = "TWO"; break;
            case 3: str = "THREE"; break;
            case 4: str = "FOUR"; break;
            case 5: str = "FIVE"; break;
            case 6: str = "SIX"; break;
            case 7: str = "SEVEN"; break;
            case 8: str = "EIGHT"; break;
            case 9: str = "NINE"; break;
            default: str = "OTHER"; break;
        }
        System.out.printf("The input integer is %s", str);
    }
}
```