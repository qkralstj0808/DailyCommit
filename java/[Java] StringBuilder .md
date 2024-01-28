# [Java] StringBuilder

자바에서 문자열하면 String을 대개 많이 떠올리고 사용할 것이다.

그런데 이 문자열이 1개 이상 있어서 이것들을 더해야 한다고 하면 어떤 방법을 쓸 수 있을까?

간단하게는 이 방법을 쓸 수 있을 것이다.

```java
public class Main
{
    public static void main(String[] args)
    {
        String result2 = "프로그래밍 - ";
        String java = "자바";
        String android = "안드로이드";
        String result = java + android;
        result2 += java += android;
        System.out.println(result);
        System.out.println(result2);
    }

}

```

이 **String 객체끼리 더하는 방법은 메모리 할당과 해제를 발생시키는데,** 덧셈 연산이 많아진다면 성능적으로 좋지 않다.

<aside>
💡 많은 문자열을 연결하면 많은 중간 문자열 객체가 생성되어 비효율적인 코드가 생성된다.

</aside>

**자바에서 String 객체는 변경 불가능하다.** 한 번 생성되면 내용을 바꿀 수 없단 뜻이다. 따라서 하나의 문자열을 다른 문자열과 연결하면 **새 문자열이 생성되고, 이전 문자열은 가비지 컬렉터로 들어간다.**

100만 개의 문자열을 연결해야 하는 상황이 왔다고 가정하자. 그리고 100만 개의 문자열을 추가로 생성했다고 하자.

문자열끼리 연결하는 작업 시에는 내부적으로 여러 작업이 발생하고, 기존 문자열 값의 길이에 추가된 문자열의 크기를 더한 크기의 새로운 문자열이 생성된다. 이걸 100만 번 수행해야 하니 메모리를 많이 잡아먹게 되는 건 당연하다. 

이를 보완하기 위해 StringBuilder를 사용할 수 있다. **Stirng은 변경 불가능한 문자열을 생성하지만 StringBuilder는 변경 가능한 문자열을 만들어 주기 때문에**, String을 합치는 작업 시 하나의 대안이 될 수 있다.

간단한 사용법은 아래와 같다.

```java
public class Main
{
    public static void main(String[] args)
    {
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append("문자열 ").append("연결");
//        String str = stringBuilder;  
// String에 StringBuilder를 그대로 넣을 순 없다. toString()을 붙여야 한다
        String str = stringBuilder.toString();
        // 두 println()은 같은 값을 출력한다
        System.out.println(stringBuilder);
        System.out.println(str);
    }

}
```

먼저 StringBuilder의 객체를 생성한 후, append()의 인자로 연결하고자 하는 문자열을 넣어서 StringBuilder의 객체를 통해 호출한다. 

그리고 출력 시에는 toString()을 붙여야 하고, String 변수에 넣을 때도 마찬가지다.

위의 예시는 일부러 결과값을 적지 않았다. 어떤 식으로 결과가 출력될지 생각해보고 직접 확인해보자.

반복문에서 StringBuilder를 사용한다면 아래와 같이 사용할 수 있다.

```java
public class Main
{
    public static void main(String[] args)
    {
        StringBuilder stringBuilder = new StringBuilder();
        ArrayList<String> list = new ArrayList<>();
        list.add("첫 번째, ");
        list.add("두 번째, ");
        list.add("세 번째, ");
        list.add("네 번째, ");
        list.add("다섯 번째");
        for (int i = 0; i < list.size(); i++)
        {
            stringBuilder.append(list.get(i));
        }
        System.out.println(stringBuilder);
    }

}
// >> 첫 번째, 두 번째, 세 번째, 네 번째, 다섯 번째
```