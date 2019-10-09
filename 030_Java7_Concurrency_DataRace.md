<!-- page_number: true -->
<!-- $theme: default -->
<!-- $size: 16:9 -->
<!-- footer: Concurrency API - Race Conditions in Java7 -->

# Java Threading
## Race Condition

---

# Race Conditions
- can occur if more than one thread try to access a shared ressource (modify, write) at the same time
- ... different threads try to _race_ each other to finish a methode


---
## Race Condition Example
 _3 Threads try to write a shared instance variable_
 - Each threads tries to increment this counter by one and afterwards decrement by one
 - Counter should keep the same value
 - Some delay is simulated by use of ```sleep()``` (In a real production system there

---
```java
class Counter  implements Runnable{
    private int c = 0;
    
    public void increment() {
        try {
            Thread.sleep(10);
        } catch (InterruptedException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
        c++;
    }
    
    public void decrement() { c--; }
    
    public int getValue() { return c; }
    
    @Override
    public void run() {
     ...
    }
}
```

---
```java
...
@Override
    public void run() {
        //incrementing
        this.increment();
        System.out.println("Value for Thread After increment " 
        + Thread.currentThread().getName() + " " + this.getValue());
        //decrementing
        this.decrement();
        System.out.println("Value for Thread at last " 
        + Thread.currentThread().getName() + " " + this.getValue());        
    }
...
```

---
```java
public class RaceConditionDemo{
    public static void main(String[] args) {
        Counter counter = new Counter();
        Thread t1 = new Thread(counter, "Thread-1");
        Thread t2 = new Thread(counter, "Thread-2");
        Thread t3 = new Thread(counter, "Thread-3");
        t1.start();
        t2.start();
        t3.start();
    }    
}
```
---
# Output
```console
Value for Thread After increment Thread-2 3
Value for Thread at last Thread-2 2
Value for Thread After increment Thread-1 2
Value for Thread at last Thread-1 1
Value for Thread After increment Thread-3 1
Value for Thread at last Thread-3 0
```
---
# Fix Race Condition
-  We need to have a way to restrict resource access to only one thread at a time
-  We have to use ```synchronized``` keyword to synchronize the access to the shared resource.

---
```java
...    
    @Override
    public void run() {
        synchronized(this){
            // incrementing
            this.increment();
            System.out.println("Value for Thread After increment " 
             + Thread.currentThread().getName() + " " + this.getValue());
            //decrementing
            this.decrement();
            System.out.println("Value for Thread at last " + Thread.currentThread().getName() 
                + " " + this.getValue());
        }        
    }
...
```

---
# Output

```console
Value for Thread After increment Thread-2 1
Value for Thread at last Thread-2 0
Value for Thread After increment Thread-3 1
Value for Thread at last Thread-3 0
Value for Thread After increment Thread-1 1
Value for Thread at last Thread-1 0
```

---
# Remarks

A code block that has a shared resource and may lead to race conditions is called a __critical section__.

Race conditions can be avoided by proper thread synchronization in critical sections.

