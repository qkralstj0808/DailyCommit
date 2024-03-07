# BufferedReader & BufferdWriter

BufferedReader

:`Scanner`와 유사.

Bufferedwriter

:`System.out.println()`;과 유사

둘은 모두 기존에 쓰던 scanner와 System.out.println()보다 속도 측면에서 훨씬 빠르기 때문에

(입력된 데이터가 바로 전달되지 않고 버퍼를 거쳐 전달되므로 데이터 처리 효율성을 높임)

많은 양의 데이터를 처리할 때 유리하다.

하지만 그에 비해 `BufferdReader은 Enter만 경계로 인식하고 받은 데이터가 String으로 고정되기 때문에 입력받은 데이터를 가공하는 작업이 필요한 경우가 많다.`

### BuffredReader 사용법

```java
BufferedReader bf = new BufferedReader(new InputStreamReader(System.in)); //선언
String s = bf.readLine(); //String
int i = Integer.parseInt(bf.readLine()); //Int
```

선언은 위에 있는 예제처럼 진행하면 된다.

입력은 readLine();이라는 메서드를 활용하는데, 여기서 반드시 주의해야할 점 2가지가 있다.

첫번째는 readLine()시 리턴값을 String으로 고정되기에 String이 아닌 다른타입으로 입력을 받을려면 형변환을 꼭 해주어야한다는 점이다.

두번째는 예외처리를 꼭 해주어야한다는 점이다. readLine을 할때마다 try & catch를 활용하여 예외처리를 해주어도 되지만 대개 throws IOException을 통하여 작업한다.

throw 이용 시

(1) 클래스를 import해주어야 한다.

*import java.io.IOException;*

(2) main 클래스 옆에 throws IOException를 작성한다.

*public static void main(String[] args) throws IOException {}*

****

```java
StringTokenizer st = new StringTokenizer(s); //StringTokenizer인자값에 입력 문자열 넣음
int a = Integer.parseInt(st.nextToken()); //첫번째 호출
int b = Integer.parseInt(st.nextToken()); //두번째 호출

String array[] = s.split(" "); //공백마다 데이터 끊어서 배열에 넣음
```

Read한 데이터는 Line단위로만 나눠지기에 공백단위로 데이터를 가공하려면 따로 작업을 해주어야하는데, 위의 두가지 방법이 대표적이다.

첫번째 방법으로는 StringTokenizer에 nextToken()함수를 쓰면 readLine()을 통해 입력받은 값을 공백단위로 구분하여 순서대로 호출할 수 있다.

두번째 방법으로는 String.split()함수를 활용하여 배열에 공백단위로 끊어서 데이터를 넣고 사용하는 방식이다..

### BufferedWriter

```java
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));   //할당된 버퍼에 값 넣어주기
String s = "abcdefg";   //출력할 문자열
bw.write(s+"\n");   //버퍼에 있는 값 전부 출력
bw.flush();   //남아있는 데이터를 모두 출력시킴
bw.close();   //스트림을 닫음
```

BufferedWriter 의 경우 버퍼를 잡아 놓았기 때문에 반드시 flush() / close() 를 반드시 호출해 주어 뒤처리를 해주어야 한다.ㅛㅛㅛㅛ

그리고 bw.write에는 System.out.println();과 같이 자동개행기능이 없기때문에 개행을 해주어야할 경우에는 \n를 통해 따로 처리해주어야 한다.