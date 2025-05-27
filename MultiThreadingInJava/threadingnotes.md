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

```java
thread.interupt() - Stops the tread if the thread in question throws an interupted exception or is handling the interupted signal explicitly (Thread.currentThread().isInterupted())
if (Thread.currentThread().isInterupted())
InteruptedException




```
## Daemon thread
- Run in background , don't become a blocker for an application if the main tread terminates . Like a text editor . If main thread terminates, the saving thread that periodically saves data doesn't have to end for the program to terminate.

```java

thread.setDaemon(true)
```




