# 1. What is multithreading and why is it important in Java?

* Multithreading is the ability of a CPU to execute multiple threads concurrently. In Java, it allows the execution of two or more parts of a program simultaneously to maximize CPU usage. It is important because it can improve the performance of applications by parallelizing tasks, making them more responsive and efficient.

# 2. Can you explain the difference between a thread and a process?

* A process is an independent program in execution with its own memory space, while a thread is a smaller unit of a process that shares the same memory space with other threads within the same process. Threads within a process can communicate more easily and share resources, whereas processes are isolated from each other.

# 3. How do you create a thread in Java?

* In Java, a thread can be created in two main ways:
  1. By extending the `Thread` class and overriding its `run` method.
  2. By implementing the `Runnable` interface and passing it to a `Thread` object.

# 4. What is synchronization in Java, and why is it necessary?

* Synchronization in Java is the capability to control the access of multiple threads to shared resources. It is necessary to prevent thread interference and consistency problems, ensuring that only one thread can access the shared resource at a time, thus maintaining data integrity.

# 5. Can you explain the differences between `synchronized` method and `synchronized` block?

* A `synchronized` method locks the entire method, meaning only one thread can execute the method at a time. A `synchronized` block, on the other hand, only locks the specified block of code, allowing more concurrency and finer control over which parts of the code are locked.

# 6. What are some common problems in multithreaded programming, and how can they be avoided?

* Common problems include deadlock, race conditions, and thread starvation.
  * Deadlock can be avoided by acquiring locks in a consistent order and using timeout for lock attempts.
  * Race conditions can be avoided by properly synchronizing access to shared resources.
  * Thread starvation can be prevented by ensuring fair scheduling of threads.

# 7. How does the `wait` and `notify` mechanism work in Java?

* The `wait` method causes the current thread to wait until another thread invokes the `notify` or `notifyAll` methods on the same object. The `notify` method wakes up a single thread that is waiting on the object's monitor, while `notifyAll` wakes up all the threads that are waiting on that object's monitor.

# 8. What is the `ExecutorService` framework, and why is it useful?

* The `ExecutorService` framework in Java provides a higher-level replacement for working with threads directly. It manages a pool of worker threads and allows for the scheduling and execution of tasks. It simplifies multithreaded programming by handling thread creation, scheduling, and lifecycle management.

# 9. Can you write a simple Java program that demonstrates thread creation and synchronization?

* Certainly! Here’s a simple Java program:

<pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

class MyThread extends Thread {
    private Counter counter;

    public MyThread(Counter counter) {
        this.counter = counter;
    }

    @Override
    public void run() {
        for (int i = 0; i < 1000; i++) {
            counter.increment();
        }
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();
        Thread t1 = new MyThread(counter);
        Thread t2 = new MyThread(counter);

        t1.start();
        t2.start();

        t1.join();
        t2.join();

        System.out.println("Count: " + counter.getCount());
    }
}</code></div></div></pre>
