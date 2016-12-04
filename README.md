#java-Thread-noSafeThread-demo

一个非线程安全的例子

```java
class NoSafeThread extends Thread {
    @Override
    public void run() {
        Safe.noSafe();
    }
}

public class Safe {
    public static void noSafe() {
        System.out.print("我的名字叫：");
        System.out.println("Leonard");
    }

    public static void main(String[] args) {
        NoSafeThread t1 = new NoSafeThread();
        NoSafeThread t2 = new NoSafeThread();
        NoSafeThread t3 = new NoSafeThread();
        t1.start();
        t2.start();
        t3.start();
    }
}
```

对多次运行代码，就可能出现下面的输出结果：
```shell
我的名字叫：我的名字叫：Leonard
我的名字叫：Leonard
Leonard
```