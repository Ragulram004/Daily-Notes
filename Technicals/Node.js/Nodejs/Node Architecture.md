- The node runs on several dependencies, the most important ones are **V8 engine** and **libuv**.
### V8
-  V8 is a fundamental part in the Node architecture. The V8 engine is what converts JavaScript code into machine code that a computer can actually understand.
### libuv
- Okay, but that V8 is not enough to create a whole server side framework like Node. And so that is why we also have libuv in Node. And libuv is an open source library with a strong focus on asynchronous IO(input/output). 
- This layer is what gives Node access to the underlying computer operating system, file system, networking, and more. 
- Besides that, libuv also implements two extremely important features of Node.JS which are the event loop and also the thread pool.
- One important thing to note here is that libuv is actually completely written in C++ and not in JavaScript.
![[Pasted image 20240811221751.png]]
### Thread and Thread Pool
- it's not important to deeply understand what a thread or a process is. That is more about computer science. Just imagine a thread as being a box where our code is executed in a computer's processor.
-  what is important to understand here, is the fact that Node runs in just one thread, which makes it easy to block Node applications. No matter if you have 10 users or 10 million users accessing your application at the same.
![[Pasted image 20240811222608.png]]
### Event Loop
![[Pasted image 20240811223659.png]]
![[Pasted image 20240811223929.png]]