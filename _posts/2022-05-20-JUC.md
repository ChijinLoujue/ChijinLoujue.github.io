# JUC

## Lock 重点
传统 synchronized 锁

可重入锁（常用） 读锁，写锁

公平锁：十分公平，先来后到
非公平锁：可以插队 （java默认）

**synchronized 和Lock的区别**   
1 synchronized 内置的java关键字， lock是一个jiava类
2 synchronized 无法判断获取锁的状态，lock 可以判断是否获取到锁
3 synchronized 会自动释放锁，lock必须要手动释放锁，如果不释放锁，会死锁
4 synchronized 线程1（获取锁、阻塞），线程2会一直等，lock锁不一定会
5 synchronized 可重入锁，不可中断，非公平；lock 可重入锁，可以判断，非公平（可以自己设置）
6 synchronized 适合锁少量代码同步，lock可以用于大量代码同步

**锁是什么 如何判断锁的是谁**


## 4 生产者和消费者的问题
