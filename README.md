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
