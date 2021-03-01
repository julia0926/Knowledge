## Lamda식
#### : 람다식은 다른말로 익명 메소드라고도 한다. 
#### (매개변수목록)->{실행문} </br> 
인터페이스 중에서 메소드를 하나만 가지고 있는 인터페이스를 함수형 인터페이스라고 한다.
쓰레드를 만들때 사용하는 Runnable 인터페이스의 경우 run()메소드를 하나만 가지고 있다.
>interface Compare 
```java
package Java.exam;

public interface Compare {
	public int compareTo(int x,int y);
}

```
>람다식 사용한 exam 클래스
```java
package Java.exam;

public class LamdaExam {
	public static void exec(Compare compare) {
		//Compare를 이용하는 exec 메소드 
		int k=10;
		int m=30;
		int value=compare.compareTo(k,m);
		System.out.println(value);
	}
	public static void main(String[] args) {
		/* exec(new Compare(){public void compareTo(int x,int y){
		 * return i>j?-1:1 ;
		 * } //람다식 안썼을 때 
		 */
		//람다식  
		exec((i,j)->{
			return i>j?-1:1 ;
		});
	}
}
```
