# JAVA 8버전 기록

## JAVA STREAM이란?

- 컬렉션, 배열 등에 저장 요소를 참조하여 반복처리 가능하게 하는 기능.

### STREAM DISTINCT란? - 리스트 중복제거를 하고싶어!!

- ORACLE 쿼리와 마찬가지로 중복을 모두 제거하여 새로운 스트림으로 반환하는 기능.

```

List<String> strings = Arrays.asList("kakao", "apple", "banana", "banana", "pineapple");

List<String> list = strings.stream().distinct().collect(Collectors.toList());

list.forEach(System.out::println);

```

실행결과
```
kakao
apple
banana
pineapple
```

### STREAM MAP이란? - 조건에 따라 값을 변경할래!!

- 람다 인자를 받아 스트림 내 요소들을 하나씩 특정 값으로 변경.

```

List<String> strings = Arrays.asList("kakao", "apple", "banana", "banana", "pineapple");

System.out.println(list.stream().map(s->s.toUpperCase().replaceAll("A","ee")).collect(Collectors.joining(" ")));

```

실행결과
```
eePPLE BeeNeeNee MELON GReePE STReeWBERRY
```

### STREAM FILTER란? 조건에 따라서 출력할래!!

- 스트림 요소를 하나씩 조건에 따라 filter하는 작업

```

ArrayList<String> list = new ArrayList<String>(Arrays.asList("Apple","Banana","Melon","Grape","Strawberry"));

List<String> stream = list.stream().filter(name -> name.contains("A")).collect(Collectors.toList());

System.out.println(stream);

```

### STREAM SORTED란?

