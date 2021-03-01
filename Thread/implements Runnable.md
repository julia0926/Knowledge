## implements Runnable
: Runnable 인터페이스 이용 </br> 스레드르 상속받는 것과 똑같으나, Runnable은 인터페이스이기 때문에 스레드르 따로 상속받아야 함.
>My thread2.java (Runnable 인터페이스 이용한 클래스)
```java
package Java.exam;

public class Mythread2 implements Runnable {
	String str;
	public Mythread2(String str) {
		this.str=str;
	}
	
	@Override
	public void run() {
		for(int i=0;i<10;i++) {
			System.out.println(str);
			try {
				Mythread.sleep((int)(Math.random()*1000));
				//1초에 한번씩 쉬었다가 출력 
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}

	}

}
```
>>ThreadExam1 (My thread2를 활용할 클래스)
```java
package Java.exam;

public class ThreadExam2 {

	public static void main(String[] args) {
		Mythread2 m1=new Mythread2("*");
		Mythread2 m2=new Mythread2("-");
		//Mythread2는 thread를 상속받지않았기 때문에(Runnable이기 때문) thread를 생성하고
		//그 안에 Mythread2를 넣어서 Thread를 생성한다.
		
		Thread t1=new Thread(m1);
		Thread t2=new Thread(m2);
		t1.start();
		t2.start();
		System.out.println("Main end!!");
	}

}
```
