# [Java] System.in.read()

Scanner, BuffredReader를 사용하지 않고 입력값을 받을 수 있다. 

버퍼(InputStream)을 사용하기 때문에 효율적이며 `IOException`의 throw를 필수적으로 해주어야 한다. 

`문자를 하나씩만` 가져올 수 있고 `아스키 코드로 변환`해 가져온다. 

예시를 들어보자 사용자가 1234를 입력하면 

```java
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {

     for(int i = 0; i < 10; i++){
         int num = System.in.read();
         System.out.print(num + " / ");
     }

    } 
}
```

각 숫자에 해당하는 아스키 코드 49부터 출력되는 것을 확인할 수 있다. (여기서 마지막 10은 Enter를 입력했기 때문에 뜬다. ) 

![Untitled](%5BJava%5D%20System%20in%20read()%20d077d2fde590497ba54df779240d7890/Untitled.png)

1) 사용자가 1234를 입력한다. 

2) 버퍼에는 49 → 50 → 51 → 52 순으로 저장된다. 

3) int num = System.in.read()를 통해 위 순서대로 값을 가져온다. 

## System.in.read() 사용

int를 통해 숫자난 단일문자 char로 값을 하나씩 가져온다. 

- 숫자로 가져올 때는 아스키 코드 번호에서 48을 빼주고
- char로 가져올 때는 아스키코드를 (char)로 재변환 해준다.

### 숫자로 가져오기

```java
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {

     for(int i = 0; i < 10; i++){
         int num = System.in.read() - 48; // 48을 빼주면 입력한 숫자를 가져옴 
         System.out.print(num + " / ");
     }

    }

}
```

![Untitled](%5BJava%5D%20System%20in%20read()%20d077d2fde590497ba54df779240d7890/Untitled%201.png)

### 문자로 가져오기

```java
import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {

     for(int i = 0; i < 10; i++){
         char c = (char) System.in.read(); // (char)로 형변환만 해준다.
         System.out.print(c + " / ");   
         
         // 엔터를 쳤기 때문에 엔터가 기록된다. 
     }

    }

}
```

![Untitled](%5BJava%5D%20System%20in%20read()%20d077d2fde590497ba54df779240d7890/Untitled%202.png)