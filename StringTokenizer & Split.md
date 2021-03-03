## StringTokenizer
: 문자열을 지정한 구분자로 쪼개주는 클래스이며, 그렇게 쪼개진 문자열을 토큰(Token)이라고 부른다.

[ 생성자 ] </br>
* **StringTokenizer(String str);** </br>
: 문자열 str을 기본 공백으로 분리한다.
* **StringTokenizer(String str,String delim);** </br> 특정 문자(delim)로 구분하여 분리한다.
* **StringTokenizer(String str,String delim,boolean returnDelims);** </br> str을 특정 delim으로 분리시키는데 그 delim까지 token으로 포함할지를 결정합니다.
* **int countTokens()** </br> 현재 남아있는 token의 개수
* **boolean hasMoreTokens()** </br> StringTokenizer는 내부적으로 어떤 위치의 토큰을 사용하였는지 기억하고 그 위치를 다음으로 옮긴다
* **Object nextElement(), String nextToken()** </br>
이 두가지 메소드는 다음의 토큰을 반환합니다. 두가지 메소드는 같은 객체를 반환하는데 반환형은 다르다. </br>nextElement는 Object를, nextToken은 String을 반환하고 있습니다. 
* **StringTokenizer(String str);** </br> 문자열 str을 기본 공백으로 분리한다.
</br>

## String[] split(String s)
: split()함수는 정규표현식 또는 특정문자를 기준으로 문자열을 나누어 배열에 저장하여 리턴한다.
* **Example 1**</br>
```java
String str="010-1234-5678";
String[] mobnum=str.split("-");

for(int i=0;i<3;i++){
  System.out.println(mobnum[i]);
}
```
* **출력**</br>
010</br>
1234</br>
5678</br>
* **Example 2**</br>
```java
String str="81-2-010-1234-5678";
String[] mobnum=str.split("-",4);
//"-"를 기준으로 4개의 배열을 
for(int i=0;i<mobnum.length;i++){
  System.out.println(mobnum[i]);
}
```
* **출력 2**</br>
81</br>
2</br>
010</br>
1234-5678</br>
