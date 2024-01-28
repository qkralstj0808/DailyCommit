# [Java] CharAt

# **1. charAt()이란?**

**Scanner는 char타입으로 입력을 받을 수 없고 String타입으로 입력받아야 한다.** 

상식적으로 생각했을 때

일반 사용자가 데이터를 입력한다고 가정하면

문자 딱 한 자만 입력하는 경우는 극히 드물 것이다.

일반적이라면 단어나 문장을 입력하는 경우가 훨씬 많을 것이기 때문에

굳이 한 글자만 입력할 수 있는 기능을 넣기 보다는

그냥 문자열(단어, 문장)로 입력받는 것이 훨씬 효율적일 것이다.

하지만 여기에서 문제가 발생한다.

바로 **char타입**을 **사용할 수 없게 되는 것**이다.

기본형 변수인 char는 단 한 글자만 저장할 수 있는 변수인데

Scanner로 입력을 받을 때는 String 타입으로 밖에 받을 수 없는 것이다.

### 그래서 등장한 것이 바로 **charAt()**이라는 녀석이다.

이 녀석은 **String으로 저장된 문자열 중에서 한 글자만 선택해서 char타입으로 변환해주는 놈**이다.

이 녀석이 존재하고 있기 때문에 우리는 Scanner를 쓰면서도 char타입을 사용할 수 있는 것이다.

그렇다면 코드에서 어떤 식으로 존재하고 있는지와

어떻게 사용하는지에 대해서 알아보도록 하자.

# **2. charAt()의 형태**

### charAt(i)

charAt 함수란?

String 타입의 데이터(문자열)에서 특정 문자를 char 타입으로 변환할 때 사용하는 함수이다.

```java
String sample = "abc";
char target = sample.charAt(0);
```

위처럼 String 변수에서 사용할 수 있으며,

charAt(i)

**i 자리에는 int 형 변수를 넣어서 원하는 위치의 문자를 가져올 수 있다.**

```java
public class Test {
	public static void main(String[] args) {
    // 변수 선언
    String example = "안녕하세요";
    char target1;
    char target2;
    char target3;

    target1 = example.charAt(0);
    target2 = example.charAt(1);
    target3 = example.charAt(2);

    System.out.println(target);
    System.out.println(target2);
    System.out.println(target3);
}
```

결과

![https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F673c2996-4b79-4218-91d0-5690b8bd732a%2Fimage.png](https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F673c2996-4b79-4218-91d0-5690b8bd732a%2Fimage.png)

## 반복문 활용 예시

**1)역순 조회**

```java
public class Test {
	public static void main(String[] args) {
    // 변수 선언
    String example = "안녕하세요";

    // 문자열 역순으로 char 변수 조회
    int exampleLength = example.length()-1;
    while (exampleLength >= 0) {
    	char target;
        target = example.charAt(exampleLength);
        System.out.println(target);
        exampleLength--;
    }
}
```

결과

![https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F0579624a-b8d5-4cb9-a11c-2644e6eeab5b%2Fimage.png](https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F0579624a-b8d5-4cb9-a11c-2644e6eeab5b%2Fimage.png)

### 2)순서대로 조회

```java
public class Test {
	public static void main(String[] args) {
    // 변수 선언
    String example = "안녕하세요";

   int i=0;
    // 문자열 순서대로 char 변수 조회
    int exampleLength = example.length()-1;
    while (i <= exampleLength) {
    	char target;
        target = example.charAt(i);
        System.out.println(target);
        i++;
    }

    // for문 활용
    for (int j=0; j<=exampleLength; j++) {
    char target;
    target = example.charAt(j);
    System.out.println(target);
    }
}
```

결과

![https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F230e1841-4c4e-4096-ac10-be5033dcb12e%2Fimage.png](https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F230e1841-4c4e-4096-ac10-be5033dcb12e%2Fimage.png)

### 사용 예시) 숫자형태의 String 에서 int 변수로 바로 변환할 때

> String 관련 코딩테스트 문제를 풀 때 꼭! 알아야하는 함수라고 한다.
> 
> 
> int num = str.charAt(i) - '0';
> 

**char 타입의 문자를 int 타입의 변수로 변환할 때 사용하는 함수**

ex)

```
String numbers = "12345";

// 숫자로 구성된 String 변수에서 특정 숫자를 바로 int 변수로 가져올 수 있다.
int targetNumber1 = numbers.charAt(0) - '0';
int targetNumber2 = numbers.charAt(1) - '0';
int targetNumber3 = numbers.charAt(2) - '0';

System.out.println("targetNumber1 = "+targetNumber1);
System.out.println("targetNumber2 = "+targetNumber2);
System.out.println("targetNumber3 = "+targetNumber3);

int test1 = 10 - targetNumber1;
int test2 = 10 - targetNumber2;
int test3 = 10 - targetNumber3;

System.out.println("10 - targetNumber1 = "+test1);
System.out.println("10 - targetNumber2 = "+test2);
System.out.println("10 - targetNumber3 = "+test3);

```

결과

![https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F9706f244-9049-4982-ab40-8081978a1d1c%2Fimage.png](https://velog.velcdn.com/images%2Fshin_stealer%2Fpost%2F9706f244-9049-4982-ab40-8081978a1d1c%2Fimage.png)