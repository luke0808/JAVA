# JAVA 기록

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

### STREAM FILTER란? - 조건에 따라서 출력할래!!

- 스트림 요소를 하나씩 조건에 따라 filter하는 작업

```

ArrayList<String> list = new ArrayList<String>(Arrays.asList("Apple","Banana","Melon","Grape","Strawberry"));

List<String> stream = list.stream().filter(name -> name.contains("A")).collect(Collectors.toList());

System.out.println(stream);

```

실행결과
```
[Apple]
```

### STREAM SORTED란? - 정렬할래!!

- 스트림을 정렬하는 기능

```

List<String> strings = Arrays.asList("kakao", "apple", "banana", "banana", "pineapple");
System.out.println(strings.stream().sorted(Comparator.comparingInt(String::length)).collect(Collectors.toList()));

List<Integer> integers = Arrays.asList(5,2,1,3,4);
System.out.println(integers.stream().sorted().collect(Collectors.toList()));
System.out.println(integers.stream().sorted(Comparator.reverseOrder()).collect(Collectors.toList()));

```


실행결과
```
[kakao, apple, banana, banana, pineapple]
[1, 2, 3, 4, 5]
[5, 4, 3, 2, 1]
```

### INTSTREAM 사용! STREAM 이용하여 , INT[] > LIST 변경하고 싶을 경우!

```
// parameter1 > [1,2,3,4,5]
// parameter1 > [1,3,5,7,8]
List<Integer> list1 = IntStream.of(parameter1).boxed().collect(Collectors.toList());
List<Integer> list2 = IntStream.of(parameter2).boxed().collect(Collectors.toList());

//*Tip 두 리스트에서 중복한 값만 도출 하는 방법은 > retainAll사용
list1.retainAll(list2);
        
System.out.println(list1);

```

실행결과
```
[1, 3, 5]
```

######################################################################################################

### Character 클래스를 사용!(내가 사용한 것만 정리)

static boolean isDigit(char ch) -> 지정된 문자가 숫자인지를 판별한다.

```

String s = "1232abdcd";
for(int i = 0; i < s.length() ; i++){
    //문자
    if(Character.isDigit(s.charAt(i)) == false){
        System.out.println(s.charAt(i) + " = 문자" );
    //숫자
    }else{
        System.out.println(s.charAt(i) + " = 숫자" );
    }
}

```

실행결과
```
1 = 숫자
2 = 숫자
3 = 숫자
2 = 숫자
a = 문자
b = 문자
d = 문자
c = 문자
d = 문자
```
