# Notes for this Udemy course.  

https://ford.udemy.com/course/java-multithreading-concurrency-performance-optimization/learn/lecture/10187964#overview 

## Os Fundamentals
- Processes (Context of the application , process ID , heap , One thread stack, files)
- Each thread stack - has it's own instruction pointer.

## What is a context switch 
- act of stoping a thread and run another is called context switch .
- TOo many thread is called **Thrashing**.
- Context switching between 2 threads in the same process is cheaper than context switching among multiple threads in different processes)

## How OS decides when to run which thread . 
- Starvation 
- OS provides a time set called epoch .
- Each epoch , can consist of multiple threads .



## How to create a thread in Java 

```java
Thread.currentThread().getName() - Name
thread.setName() - To set the thread name

Thread.sleep(1000) - Don't schedule the thread until the time pass.
thread.setPriority(Thread.MAX_PRIORITY) 

```
## How to visually debug
What thread is running in the backgrounds when you debug an application . 
- Finalizer
- ReferenceHandler
- Signal Dispatcher 

## How to provide an exception handler for a thread which has a uncaught exception

```java
Thead thread = new Thread(new Runnable() {

  @Override
  public void run(){}
});

thead.setUncaughtExceptionHandler(new Thread.UncaughtExceptionHandler(){

   @Override
    public void uncaughtException(Thread t, Throwable e){
        System.out.println("A critical error Happened");
    } 
    

});

  thread.start();


```
## Thread termination - Why and when ? 

thread.interupt() - Stops the tread if the thread in question throws an interupted exception or is handling the interupted signal explicitly (Thread.currentThread().isInterupted())

```java
if (Thread.currentThread().isInterupted())
InteruptedException




```
## Daemon thread
- Run in background , don't become a blocker for an application if the main tread terminates . Like a text editor . If main thread terminates, the saving thread that periodically saves data doesn't have to end for the program to terminate.

```java

thread.setDaemon(true)
```

## Thread join 

If we do a thread B check for thread A is finished the checking is taking a lot of CPU cycles. 

-- Busy wait way
```java
factorialThread.isFinished()
```

-- TheadJoin 

```java
thread.join()
```

-- If I don't wait for more than 2 sec
```java
thread.join(2000)
```

### An example of thread join using Big Integer. 

```java
import java.math.BigInteger;

public class ComplexCalculation {
    public BigInteger calculateResult(BigInteger base1, BigInteger power1, BigInteger base2, BigInteger power2) {
        BigInteger result = BigInteger.valueOf(0);
        /*
            Calculate result = ( base1 ^ power1 ) + (base2 ^ power2).
            Where each calculation in (..) is calculated on a different thread
        */
        
        PowerCalculatingThread pct1 = new PowerCalculatingThread(base1, power1);
        
        PowerCalculatingThread pct2 = new PowerCalculatingThread(base2, power2);
        
        try {
            pct1.start();
            pct1.join(2000);
            pct2.start();
            pct2.join(2000);
        }
        catch(InterruptedException e){
            return result;
        }
        
        
        result = pct1.getResult().add(pct2.getResult());
        
        return result;
    }

    private static class PowerCalculatingThread extends Thread {
        private BigInteger result = BigInteger.ONE;
        private BigInteger base;
        private BigInteger power;
    
        public PowerCalculatingThread(BigInteger base, BigInteger power) {
            this.base = base;
            this.power = power;
        }
    
        @Override
        public void run() {
           /*
           Implement the calculation of result = base ^ power
           */
           
           for(BigInteger i = BigInteger.valueOf(0) ; i.compareTo(power) < 0  ; i = i.add(BigInteger.valueOf(1))){
               
               this.result = this.result.multiply(base);
               
           }
           
           
           
        }
    
        public BigInteger getResult() { return result; }
    }
}

```
## Stack vs Heap 

Method is placed in stack in stack frame . Heap is shared by all stack. Anything that is allocated by new  is placed in heap. Members of a class , irrespective of whether primitive or not is stored in the heap. Static variables are stored in heap. Managed by the garbaze collector. 

References are not object. References can be sometimes placed on the stack and sometime on the heap depending on where they are. 





