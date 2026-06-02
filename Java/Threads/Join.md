```Java
class CalculationThread extends Thread {
    private String type;

    CalculationThread(String type) {
        this.type = type;
    }

    public void run() {
        try {
            System.out.println(type + " thread is now RUNNING.");
            // sleep() moves the thread to a BLOCKED/WAITING state for a set time
            Thread.sleep(1000); 
            System.out.println(type + " thread has finished its task.");
        } catch (InterruptedException e) {
            System.out.println(e);
        }
    }
}

public class ThreadStateDemo {
    public static void main(String[] args) {
        // NEW state: Object created but not yet started
        CalculationThread t1 = new CalculationThread("Even Sum");
        CalculationThread t2 = new CalculationThread("Odd Sum");

        // start() moves threads to the RUNNABLE state
        t1.start();
        t2.start();

        try {
            // join() makes the main thread wait for t1 and t2 to reach the DEAD state
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            System.out.println(e);
        }

        System.out.println("Main thread resumes after sub-threads have TERMINATED.");
    }
}
```