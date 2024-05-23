# Stream API

### StreamAPI란?

자바의 람다식을 이용해서 컬렉션 데이터를 효율적으로 가공할 수 있는 인터페이스다. 대표적으로 필터링, 매핑, 정렬, 집계 등의 작업이 있다.

### 장점

데이터를 가공하여 필요한 데이터를 추출하고 싶을때 함수나 코드를 따로 작성하면 번거로울 뿐만 아니라 재사용성이 떨어진다. 이때, Stream API를 사용하면 메모리도 절약되고 쉽게 필요한 데이터를 추출 할 수 있다.

### Stream의 타입별 객체

|    타입    |        객체        |
| :--------: | :----------------: |
|    byte    |   Stream\<Byte>    |
|   short    |   Stream\<Short>   |
|  **int**   |   **IntStream**    |
|  **long**  |   **LongStream**   |
|    char    | Stream\<Character> |
|   float    |   Stream\<Float>   |
| **dobule** |  **DoubleStream**  |
|   String   |  Stream\<String>   |
|  boolean   |  Stream\<Boolean>  |

### Stream의 특징

`내부 반복` : Stream은 내부적으로 반복하기 때문에 따로 반복문을 사용할 필요가 없다. <br>
`일회성` : Stream은 재사용이 불가능 하고 일회성으로 사용한다.<br>
`원본데이터 보호` : Stream은 따로 객체를 만들어서 사용하기 때문에 원본 데이터에 영향을 끼치지 않는다. <br>
`람다식` : Stream안에 들어가는 식은 람다식으로 표현한다.

### Stream API의 사용법

Stream 생성 -> 중간 연산 -> 최종 연산 과정으로 진행된다.

#### Stream 생성

|       분류       | 생성                                                          |
| :--------------: | :------------------------------------------------------------ |
|   empty stream   | Stream.empty();                                               |
|    Collection    | ArrayList.stream();                                           |
|      Array       | Arrays.stream(arr);                                           |
|     builder      | Stream.<String>builder().add("a").build();                    |
|     generate     | Stream.generate(() -> "a").limit(3);                          |
|     Iterator     | Stream.iterate(70, (n) -> n + 10).limit(3)                    |
| 기본 타입 스트림 | IntStream intStream = IntStream.range(1, 5);                  |
|   파일 스트림    | Files.lines(Paths.get("file.txt"), Charset.forName("UTF-8")); |

#### 중간 연산

|         분류          | 생성                 |
| :-------------------: | :------------------- |
|      Stream 필터      | filter(), distinct() |
|      Stream 변환      | map(), flatMap()     |
|      Stream 제한      | limit(), skip()      |
|      Stream 정렬      | sorted()             |
| Stream 연산 결과 확인 | peek()               |

#### 최종 연산

|    분류     | 생성                                |
| :---------: | :---------------------------------- |
| 요소의 출력 | forEach()                           |
| 요소의 검색 | findFirst(), findAny()              |
| 요소의 검사 | anyMatch(), allMatch(), noneMatch() |
| 요소의 통계 | count(), min(), max()               |
| 요소의 연산 | sum(), average()                    |
| 요소의 수집 | collect()                           |

### 예제

```
//*****Stream에서 추출한 데이터를 List에 저장하는 경우*****

List<String> noobs;

//stream 생성
Stream<String> a = member.stream();
//기본적으로 Collection은 stream()을 지원함

noobs = a.distinct()
.filter(s -> s.contains("신입")) //filter를 사용해서 신입 회원 필터링한다.
.map(s -> s.substring(s.indexOf("-")+1)).toList();

//map을 통해 데이터를 변환시켜서 리스트에 저장한다.
//Stream으로 추출한 데이터를 바로 Collection에 저장하면 오류가 난다.
//이유는 Collection과 Stream객체는 타입이 다르기 때문이다.
//Collection의 toList()함수를 통해 리스트로 변환해서 넣어준다.


//****Stream에서 나온 데이터를 바로 출력하는 경우*****

//Stream은 한번 사용하면 닫히기 때문에 다른 Stream을 생성해 준다.
Stream<String> b = member.stream();

b.filter(x -> x.contains("신입"))
.map(s -> s.substring(s.indexOf("-")+1))
.forEach( s -> System.out.println(s+"님 안녕하세요!"));
//forEach는 Stream객체를 출력해준다.
```
