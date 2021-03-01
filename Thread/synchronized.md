## synchronized 
: 동기화를 위한 장치로서, 임의의 코드 블록을 동기화가 설정된 임계영역으로 지정한다.
## wait(), notify()
: synchronized를 사용해도 여전히 동기화가 필요하 때(두 스레드가 동시에 접근할 때) 필요하다
1. wait() : 다른 스레드가 이 객체의 notify()를 불러줄 때까지 대기
2. notify() : 이 객체에 대기 중인 스레드를 깨워 RUNNABLE 상태로 만든다. 2개 이상의 스레드가 대기중이라도 오직 1개만 깨움.
>ThreadB.java (thread를 상속한 클래스)
```java
package Java.exam;

public class ThreadB extends Thread {
	int total;

	@Override
	public void run() {
		//이 코드가 실핼할 때 다른 스레드가 실행하고자 하면
		//실행하고 있는 스레드가 끝날때까지 대기상태  
		synchronized(this){ 
			for(int i=0;i<5;i++) {
				System.out.println(i+"를 더합니다.");
				total+=i;
				try {
					Thread.sleep(1000);
				} catch (InterruptedException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
			notify();//wait하고 있는 thread를 깨움. 
		}

	}
	
}

```
>ThreadA.java (B를 사용해서 wait함)
```java
package Java.exam;

public class ThreadA {

	public static void main(String[] args) {
		ThreadB thread=new ThreadB();
		thread.start();
		//thread에 대해서 동기화 블록을 설정 
		synchronized(thread) {
			try {
				System.out.println("b가 완료될 때까지 기다립니다.");
				thread.wait();
			} catch (InterruptedException e) {
			// TODO Auto-generated catch block	
				e.printStackTrace();	
			}
			System.out.println("total is : "+thread.total);
		}
	}
}

```
