# 헷갈리는 부분

- 배열의 길이(메소드에 괄호x): arr.length
- String의 길이(메소드에 괄호o): st.length()
- 컬렉션의 길이: list.size()

### 형 변환 메소드

| 역할 | 메소드 |
| --- | --- |
| char → String | Character.toString(문자1개); |
| String → char | s.charAt(인덱스) |
| char array → String | String.valueOf(char 배열); |
| String → char array | s.toCharArray(); |
| int → String | String.valueOf(정수1개) |
| String → int | Integer.parseInt(문자열); |

# 입출력

### 입력

1. BufferedReader
- 문자열 입력

```java
//1개
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

String input = br.readLine();
```

- 문자열 여러개 입력

```java
// 여러개 문자열
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String[] input = br.readLine().split(" ");
```

- 정수 입력받기

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
int n = Integer.parseInt(buffer.readLine());
```

- 공백으로 구분된 정수 입력

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String[] input = br.readLine().split(" ");
int n1 = Integer.parseInt(intput[0]);
int n2 = Integer.parseInt(intput[1]);
...

```

- 공백으로 구분되지 않은 정수 입력
    
    charAt에다가 ‘0’을 빼줌으로써 int 배열에 입력가능. 여기서 char는 자동으로 int로 변환된다.
    

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
map = new int [n][n];
for(int i=0; i<n; i++){
    String str = br.readLine();
    for(int j=0; j<n ; j++){
        map[i][j] = str.charAt(j)-'0';
    }
}
```

- 문자 입력

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String s = br.readLine();
for (int i = 0; i < n; i++) {
     map[i] = s.charAt(i);
}
```

- String 배열 → char

```java
String[] strs

map = new char[str 개수][각 str 길이];
// matrix에 값 추가

for (int j=0; j<str 개수; j++) {
    map[j] = strs[j].toCharArray();
}
```

1. StringTokenizer
- 공백이 있을 때 뒤에 문자열이 공백처리를 땡겨 채우도록 한다.
- **StringTokenizer가 BufferedReader보다 빠르게 사용 될 수 있다**

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
StringTokenizer st = new StringTokenizer(br.readLine());

String A = st.nextToken();
String B = st.nextToken();
String C = st.nextToken();
String D = st.nextToken();
```

1. Scanner
- 젤 느림

### 출력

1. BufferedWriter

```java
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out)); // 선언
String str = "abcdef"; // 출력할 문자열
bw.write(s); // 출력
bw.newLine(); // 줄바꿈
bw.flush(); // 남아있는 데이터 모두 출력
bw.close();
```

BufferedWriter는 버퍼를 잡아 놓은 것이기에 반드시 사용후에 flush()/close()를 해주어야한다. close()를 하게되면 출력 스트림을 아예 닫아버리기 때문에 한번 출력후에 다른 것도 출력하고자 한다면 flush()를 사용하면 된다

- write 안에는 String으로 써줘야함
    
    ```java
    	bw.write(String.valueOf(answer));
    ```
    

**2. StringBuilder**

- 그냥 문자열이기 때문에 매우 간단하다
- 모아뒀다 한번에 출력 가능

```java
StringBuilder sb = new StringBuilder();
sb.append("a");
sb.append("b").append(" ");
sb.append("c").append("\n");
System.out.println(sb);
```

1. System.out.println(””)

1. 컬렉션에 저장된 값 ‘\n’을 구분자로 한번에 출력

```java
//set일 경우
set.forEach(System.out::println);
```

- 배열과 리스트 차이
    - **배열**: 데이터의 크기가 정해져 있고, 추가적인 삽입 삭제가 일어나지 않으며 검색을 필요로 할 때 유리하다.
    - **리스트**: 데이터의 크기가 가변적이고, 삽입 삭제가 많이 일어나며, 검색이 적은 경우에 유리하다.

# 배열

### 최대값

1. stream 이용

```java
int max = Arrays.stream(arr).max().getAsInt();
```

### 평균값

1. stream 이용

```java
double average = Arrays.stream(arr).average().orElse(0);
```

### 합

1. stream 이용

```java
int sum = Arrays.stream(arr).sum();
```

### 일괄 초기화

```java
 Arrays.fill(배열명, 초기화할 값);
```

### 정렬

```java
Arrays.sort(배열명);
```

- 이차원 배열 첫번째 요소로 정렬

```java
Arrays.sort(coin, Comparator.comparingInt(a -> a[0]));
```

### 복사

- 반복문보다 성능 떨어지지만 간결함

```java
Arrays.copyOf(배열명, 길이);
```

### 일차원 배열 복사

```java
arr.clone();
```

### 이차원 배열 복사

- 깊은 복사: 주소값 참조가 아니라 데이터만 옮겨옴

```java
for(int i=0;i<n;i++) {
	arrCopy[i] = arr[i].clone();
}
```

### 부분 복사

```java
Arrays.copyOfRange(array, from, to);
```

- from: 해당 위치 포함O
- to: 해당 위치 포함X

### 가변배열

- 2차원에서 두번째 요소 값은 가변적임
- 요소 추가 가능

```java
  char[][] room = new char[i][];
```

# String

### 인덱스의 문자 반환

```jsx
char temp = str.charAt(i) // i: 인덱스
```

### 특정 구분 기호를 사용하여 문자열 컬렉션 결합

```java
String.join(구분자, 컬렉션명);
//컬렉션명: 배열 등등 
```

### 붙어있는 문자 배열에 분리

- String 배열에 분리

```java
String [] arr = str.split(""); // String 배열에 분리
```

- Char 배열에 분리

```java
char [] arr = str.toCharArray();
```

# 이진 탐색

### 배열

```java
Arrays.binarySearch()
```

### 리스트

```java
Collections.binarySearch()
```

- 찾는 값 있을 때 반환값: 인덱스
- 찾는 값 없을 때 반환값: 음수
    - 들어가야 하는 인덱스 값: -index - 1

# Map

### 기본 메소드

| 메소드 | 형식 | 반환값 | 기능 |
| --- | --- | --- | --- |
| put | put(K key, V value) |  | 추가 |
| get | get(Object key) | value/null | 값 얻기 |
| containsKey | containsKey(Object key) | true/ false | 키 포함 여부 |
| containsValue | containsValue(Object value) | true/ false | 값 포함 여부 |
| size | size() | 키-값 매핑 수 | 크기 |
|  | remove(Object key) |  | 삭제 |
|  | values() | Collection<T> | 포함된 Collection 뷰를 반환 |
|  |  |  |  |
|  |  |  |  |

### putIfAbsent

- 해당 키가 없으면 추가 & null 반환
- 키가 있고 null 아니면 현재값 반환
- 키가 있고 null이면 키 업데이트 & null반환

```java
Map.putIfAbsent(key, value);
```

### 반복

```
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    String key = entry.getKey();
    Integer value = entry.getValue();
    System.out.println("Key: " + key + ", Value: " + value);
}
```

# List

### 기본 메서드

| 메소드 | 형식 | 반환값 | 기능 |
| --- | --- | --- | --- |
| add | add(E 요소) |  | 끝에 추가 |
| get | get(int index) | 위치에 해당하는 값 | 지정 위치 요소 반환 |
|  | remove(int index) |  | 제거 |
|  | size() | 요소 수 | 크기 |
|  | contains(Object element) | true/false |  |
|  | addAll(Collection<? extends E> collection) |  | 컬렉션의 모든 요소 끝에 추가 |
|  | clear() |  | 전체 제거 |
|  | indexOf(Object element) | 처음 나타나는 인덱스/-1 | 원소의 인덱스 찾기 |
|  | isEmpty() | true/false | 원소 존재 확인 |
|  | set(int index, E element) |  | 대체 |

# SET

- 용도: 중복 제거

### TreeSet

- **String순**으로 정렬할 때 사용
- 기본적으로 오름차순 정렬

LinkedHashSet

- **int순으로** 정렬할 때 사용
- 입력순으로 정렬

# Consumer<T>

- 사용
    - **java.util.function**
    - **`Consumer`** 인터페이스는 단일 입력 인수를 취하고 결과를 반환하지 않고 일부 작업을 수행(매개값을 소비하는 역할 ) = 각 요소에 적용되는 동작을 정의해서 간단히 사용
    - 조건
        1. 컬렉션이나 스트림의 각 요소에 적용해야 하는 동작을 정의해야 할 때
        2. 문자열에서 작동하는 코드 조각을 캡슐화
        3. 목록 반복시 루프 대체

- 메소드

```java
void accept(T t);
```

- 예시 코드

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Define a Consumer to print each name - 반복되는 부분 = 각 요소에 적용되는 동작
Consumer<String> printName = (String name) -> System.out.println("Hello, " + name);

// Apply the Consumer to each element in the list
names.forEach(printName);
```

- 출력

```java
Hello, Alice
Hello, Bob
Hello, Charlie
```

- forEach
    - 루프를 사용하여 명시적으로 반복할 필요 없이 컬렉션의 각 요소에 대해 특정 작업을 수행
    - 컬렉션의 반복자가 제공하는 순서대로 반복

```java
void forEach(Consumer<? super T> action);
```

```java
/* 
	유형: 이분탐색
    문제: 문의조건 쿼리 주어질 때 조건에 해당하는 사람 수 출력
        - 문의조건의 종류
            개발언어, 직군, 경력, 소울푸드, 점수
        
    단서: 효율성 & 탐색고려. O(NM)이니까 50,000*100,000= 5*10^9임. 50억이므로 너무 큼 -> 이진 탐색, 점수 정렬 가능 
    알고리즘: 
    1. 입력
         [] info, 지원자 정보
         [] query, 문의 조건
         scoresMap : k: 검색 조건(문자열), v: 점수(정수)
        
    2. 전처리: 지원자 정보에서 조건별 리스트 생성
        1. 지원자 정보중 맞는 조건의 리스트 찾기
            forEachKey()
        2. 정렬 
    3. 지원자 수 세기
        1. 이분탐색
    4. 출력

 	시간복잡도: 
	레퍼런스: <프로그래머스 코딩테스트 문제풀이 전략:자바편>
    주의:
    시간: 3
    보완: 구현
*/

class Solution {
    
    // 2. 전처리: info -> 조건별 리스트 생성
    private Map<String, List<Integer>> buildScoresMap(String[] info){ // info 배열 받아와서 Map으로 반환할 것 
        Map<String, List<Integer>> scoresMap = new HashMap<>(); //점수에 대한 map을만든다.
        
        // 2-1 지원자 정보 중 맞는 조건의 리스트 찾기
        for(String s : info){ //info를 하나씩 꺼내봄
            String[] tokens = s.split(" "); // 스페이스바를 기준으로 토큰 받아옴 
            int score = Integer.paresInt(tokens[tokens.length - 1]); //맨 마지막 토큰(점수) 정수로 변환
            forEachKey(0,"", tokens, key->{scoresMap.putIfAbsent(key,new ArrayList<>()); 
                                          scoresMap.get(key).add(score);})
        }
        
        // 2-2 정렬
        for(List<Integer> list : scoresMap.values()){
            Collections.sort(list);
        }
        
        return scoresMap;
    }
    
    
    // 2-1 만들 수 있는 모든 조건 찾기
    private void forEachKey(int index, String prefix, String[] tokens, Consumer<String> action){
        if(index == tokens.length -1){
            action.accept(prefix);
            return;
        }
        forEachKey(index+1, prefix + tokens[index], tokens, action);
        forEachKey(index+1, prefix + "-", tokens, action);
    }
    
    // 3-1 이분탐색 - 지원자수 찾기
    private int binarySearch(int score, List<Integer> scores){
        int start =0;
        int end = scores.size() -1;
        
        //이진 탐색
        /*
        예시:
        1 3 5 찾는값은 2 
        첫시행)
            mid = (0+2)/2 = 1
            if(3 >= 2){
                end = 1 이 된다.
            }
        두번째 시행) start =0, end =1
            mid = (0+1)/ 2 = 0
            if(1 >= 2)가 아니니까
            else{
                start = 0 +1 = 1 이 된다
            }
        세번째 시행) start =1, end =1이니까 반복문 종료
        
        
        if(3<2)가 아니니까 
            start = 1 반환 
            
            
        예시2:
        1 3 5 찾는 값은 3
        첫시행)
            mid = (0+2)/2 = 1 
            if(3 >=3){
                end = 1
            }
        두번째 시행) start=0, end =1
            mid = (0+1)/2 =0
            if(1>=3)이 아니니까 
            else{
                start = 0+1 = 1
            }
        세번째 시행) start=end=1 이라서 루프 탈출
        if(3<3)이 아니니까
            start = 1반환
        
        */
        while (end> start){
            int mid = (start+end) /2 ; //중간값
            
            if(scores.get(mid) >= socre){ // 중간보다 작거나 같은 범위내에 있으면
                end = mid; //오른쪽 끝을 줄인다.
            }else{
                start = mid +1; // 중간값보다 큰 범위 내에 있으면 왼쪽 끝을 땡김.
            }
        }
        
        //마지막 남은 원소가 조건을 만족하는지 확인 
        if(scores.get(start) < score){ // 시작값보다 큰 범위에 있으면 
            return scores.size(); // 마지막 인덱스 +1 위치
        }
        return start;
    }
    
    //3.조건에 맞는 지원자 수 세기
    private int count(String query, Map<String, List<Integer>> scoresMap){
        String[] tokens = query.split(" (and )?");
        
        String key = String.join("", Arrays.copyOf(tokens, tokens.length -1)); // 마지막 원소는 제외하고 전달
        if(!scoresMap.containsKey(key)) return 0;
        List<Integer> scores = scoresMap.get(key);
        
        int score = Integer.parseInt(tokens[tokens.length -1]);
        
        return socres.size() - binarySearch(score, socresMap.get(key));
            
    }
    
    public int[] solution(String[] info, String[] query) {
        //전처리
        Map<String, List<Integer>> scoresMap = buildScoresMap(info);
    
        //출력
        int[] answer = new int[query.length];
        for(int i=0;i<answer.length; i++){
            answer[i] = count(query[i], scoresMap);
        }

        return answer;
    }
    
    
    
    
}
```

### for문과 향상된 for문 선택기준

- for문
    - 컬렉션에 저장 할 때
    - i 인덱스가 필요할 때
- 향상된 for문
    - 컬렉션의 값 읽을 때
    
    ```
    4 2
    9 8 7 1
    ```
    
    - i 인덱스 필요X
    

# 우선순위 큐

### 최소힙

```java
  PriorityQueue<Integer> q = new PriorityQueue<>();
```

### 최대힙

```java
  PriorityQueue<Integer> q = new PriorityQueue<>(Collections.reverseOrder());
```

# Stream

```java
 .filter(n -> (n%2 == 0)) // 조건 필터링 
 .collect(Collectors.toSet()); // Collectors 사용
```

```java
.mapToInt(Integer::intValue) // Integer를 int value로 변환
.boxed() // Stream<Integer>로 변환(sorted 지정해주려면 필요) 
```

```java
.chars()  //String을 IntStream으로 변환(문자지만 char또한 정수라 통합해 다룸) 
```

- **`.map(Integer::parseInt)`**는 본질적으로 **`.map(s -> Integer.parseInt(s))`**와 같다 = 람다식에서 매개변수 없애기 적용

- 형 변환

| from | to | 문법 |
| --- | --- | --- |
| String [] | Integer Collection |  Arrays
.stream(str) // 스트림화
.map(Integer::parseInt) // 각각을 정수로 변환
.collect(Collectors.toList()); // 여기선 List |
| String [] | int [] | int[] intArray = 
Arrays.stream(stringArray)
.mapToInt(Integer::parseInt) // String을 int로 (.map은 Stream<> 반환, 이건 메모리 효율성 높은 IntSream으로 반환)
.toArray(); // 배열로 |
| String | int [] | int[] integers =
str.chars() // IntStream 얻음
.map(Character::getNumericValue) // Map each code point to its numeric value
.toArray(); 
 |

# 정렬

- n번째 문자로 정렬

```java
Arrays.sort(strings, (s1, s2) -> s1.charAt(n) - s2.charAt(n));
```

```java
Arrays.sort(strings, Comparator.comparingInt(s -> s.charAt(n));
```

- 오름차순 비교기

```java
**s1.compareTo(s2);**
```

### set, map 반복

```java

       // 방법 1: entrySet()을 이용한 반복
      for (Map.Entry<String, Integer> entry : map.entrySet()) {
          String key = entry.getKey();
          Integer value = entry.getValue();
          System.out.println("Key: " + key + ", Value: " + value);
      }

      // 방법 2: keySet()을 이용한 반복
      for (String key : map.keySet()) {
          Integer value = map.get(key);
          System.out.println("Key: " + key + ", Value: " + value);
      }

      // 방법 3: values()를 이용한 반복
      for (Integer value : map.values()) {
          System.out.println("Value: " + value);
      }
```

### 리스트를 int 배열로 변경

```java
int[] array = list.stream().mapToInt(Integer::intValue).toArray();
```
