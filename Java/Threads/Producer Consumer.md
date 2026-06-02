```Java
class SharedBuffer {
    private int data;
    private boolean available = false;

    // Method for the consumer to get data
    public synchronized int consume() {
        while (!available) {
            try {
                // wait() causes the thread to wait until the producer calls notify() [1]
                wait(); 
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
        available = false;
        System.out.println("Consumed: " + data);
        // notify() signals the producer that the buffer is now empty [1]
        notify(); 
        return data;
    }

    // Method for the producer to put data
    public synchronized void produce(int value) {
        while (available) {
            try {
                // wait() causes the thread to wait if data hasn't been consumed yet
                wait(); 
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
        data = value;
        available = true;
        System.out.println("Produced: " + data);
        // notify() signals the consumer that new data is available [1]
        notify(); 
    }
}

class Producer extends Thread {
    SharedBuffer buffer;
    Producer(SharedBuffer b) { this.buffer = b; }

    public void run() {
        for (int i = 1; i <= 5; i++) {
            buffer.produce(i);
        }
    }
}

class Consumer extends Thread {
    SharedBuffer buffer;
    Consumer(SharedBuffer b) { this.buffer = b; }

    public void run() {
        for (int i = 1; i <= 5; i++) {
            buffer.consume();
        }
    }
}

public class ProducerConsumerDemo {
    public static void main(String[] args) {
        SharedBuffer buffer = new SharedBuffer();
        Producer p = new Producer(buffer);
        Consumer c = new Consumer(buffer);

        // start() moves the threads to the Runnable state [3]
        p.start();
        c.start();
    }
}
```