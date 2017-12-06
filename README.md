# TestingProject For Synchronisation
package com.Thread;

class Display{
	public synchronized void show(String name){
		for(int i = 0; i < 5; i++){
			try {
				Thread.sleep(2000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			System.out.println("Hello : "+name);
		}
	}
}

class MyThread extends Thread{
	
	Display d;
	String name;
	
	public MyThread(Display d, String n){
		this.d = d;
		this.name = n;
	}
	
	public void run(){
		d.show(name);
	}
}


public class SynchronisedDemo {

	public static void main(String[] args) {
		Display d = new Display();
		MyThread mt = new MyThread(d, "Mohan");
		MyThread mt1 = new MyThread(d, "Anjan");
		
		mt.start();
		mt1.start();

	}

}

