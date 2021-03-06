#PV操作-难点

PV操作是操作系统课程中的难点，应用较为灵活，要理解它在进程并发过程中，所起到的作用。

**临界资源**：进程间需要互斥方式进行共享访问的资源，比如打印机、磁带机等（比如前面的**独木桥**就相当于一个临界资源）；

**临界区**：通俗来讲临界区是一个**代码段**，它是每个进程中访问临界资源的那段代码；

**信号量**：PV操作中离不开信号量，比如P(S)、V(S)，其中的S就是信号量，它是主要应用于PV操作中的一种专属变量。

![](/imgs/1.3.4-1PV操作.png)

#具体问题-深入理解PV操作

###1. 如果没有PV操作，会产生什么问题？

以单缓冲区为例，如果没有PV操作，那么生产者在生产产品送入到缓冲区时，就又可以溢出，而消费者在从缓冲区取出产品的时候，也会面临没有产品可取的情况。

![](/imgs/1.3.4-2深入理解PV操作.png)

###2. 引入PV操作

解决了并发进程之间某些先后约束关系，分析如下。

先来看生产者先执行的情况：

当生产者第一次执行任务时，分别执行了一次P(S1)操作和一次V(S2)操作后，S1=1-1=0、S2=0+1=1，那么当生产者第二次执行任务时，生产第二个产品，再次执行一次P操作后，S1=0-1=-1，那么就会把当前的生产者进程就会被送入进程的等待队列中阻塞，那么第二次生产的产品就不会被送入缓冲区，也就不会产生溢出；

当生产者进程阻塞之后，当前S2=1，消费者进程开始执行P(S2)操作，S2=1-1=0，P操作结果不小于0,消费者从缓冲区中取产品，此时缓冲区变空，消费者再继续执行V(S1)操作，S1=-1+1=0满足<=0,那么就从进程等待队列中唤醒一个进程（即生产者进程），此时生产者进程就可以继续执行了；

再来看消费者先执行的情况，由于S2初值为0，消费者一开始执行，先进行P(S2)操作，S2=0-1=-1<0，此时消费者进程就会被阻塞，也就不会继续执行，从而避免执行发生错误；

![](/imgs/1.3.4-3深入理解PV操作.png)
