# [[Multithreading]]

run tasks in chunks

code, data and files are shared with multithread

yield - like car/makes tread lower priority 
join - wait for thread to finish before starting other threads/processes/make it high priority/top of the running stack


10 tasks max

thread pool vs makimg new threads?

run needs to have stuff in it so threads know which method to run

if  more tasks than threads in poll, extra tasks will wait for first tasks to finish

race condition?

synchronized locks critical region/resource all threads use to taake turrns

reertrant lock?

condition?

guarantees longest waitng thread gets the lock first

deadlock?

We can make a thread by either one of two ways:
- using `extneds Thread` in the class definition
- using `implements Runnable` in the class definition
	- this requires you to implement a `run()` method in the class


