## extends Thread 

>My thread.java (thread를 상속한 클래스)
```java
package Java.exam;

public class Mythread extends Thread {
	String str;
	public Mythread(String str) {
		this.str=str;
	}
	@Override
	public void run() {
		for(int i=0;i<10;i++){
			
			try {
				System.out.println(str);
				Thread.sleep((int)(Math.random()*1000));
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
	//run()을 오버라이딩해서 str을 출력하되 너무 빨리 출력되므로 잠깐 쉬었다가
	//출력되게 하였다.
	
}

```
>ThreadExam1 (My thread를 활용할 클래스)
```java
package Java.exam;

public class ThreadExam1 {

	public static void main(String[] args) {
		Mythread t1=new Mythread("*");
		Mythread t2=new Mythread("-");
		
		t1.run();
		t2.run();
		System.out.println("main end!!");
	}

}

```
