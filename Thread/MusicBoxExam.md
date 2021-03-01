## 하나의 스레드와 공유객체 
#### 하나의 객체를 여러개의 Thread가 사용한다는 것을 의미
- 공유객체 MusicBox를 이용해서 사용자 3명을 만들어 사용하기

>MusicBox.java (공유 객체)
```java
package Java.exam;

public class MusicBox {
	//공유 객체 
	public void playMusicA() {
		for(int i=0;i<10;i++) {
			System.out.println("1. Honne's song");
			try {
				Thread.sleep((int)(Math.random()*1000));
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
	}
	public void playMusicB() {
		for(int i=0;i<10;i++) {
			System.out.println("2. BTS's song");
			try {
				Thread.sleep((int)(Math.random()*1000));
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
	}
	public void playMusicC() {
		for(int i=0;i<10;i++) {
			System.out.println("3. Shinee's song");
			try {
				Thread.sleep((int)(Math.random()*1000));
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		
	}
}
```

>MusicPlayer.java (MusicBox를 가지는 thread)
```java
package Java.exam;

public class MusicPlayer extends Thread {
	int type;
	MusicBox mb;
	//생성자로 부터 MusicBox와 정수 하나를 받아 필드 초기화
	public MusicPlayer(int type,MusicBox mb) {
		this.type=type;
		this.mb=mb;
	}
	@Override
	public void run() {
		switch(type) {
			case 1:mb.playMusicA(); break;
			case 2:mb.playMusicB(); break;
			case 3:mb.playMusicC(); break;
		}
	}
}
```
>MusicBoxExam.java (MusicBox와 MusicPlayer를 생성하여 이용한 main)
```java
package Java.exam;

public class MusicBoxExam1 {

	public static void main(String[] args) {
		
		MusicBox box=new MusicBox();
		
		MusicPlayer kim=new MusicPlayer(1,box);
		MusicPlayer lee=new MusicPlayer(2,box);
		MusicPlayer jin=new MusicPlayer(3,box);
		
		kim.start();
		lee.start();
		jin.start();
	}

}
```
