# Stream API

### 개요

Stream API란 자바의 람다식을 이용해서 컬렉션 데이터를 효율적으로 가공할 수 있는 인터페이스다. 대표적으로 필터링, 매핑, 정렬, 집계 등의 작업이 있다.

### Stream의 타입별 객체

|    타입    |        객체        |
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
`일회성` : Stream은 재사용이 불가능 하고 일회성으로 사용한다.
`원본데이터 보호` : Stream은 따로 객체를 만들어서 사용하기 때문에 원본 데이터에 영향을 끼치지 않는다.
