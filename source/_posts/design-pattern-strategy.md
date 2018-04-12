---
title: 设计模式（二）策略模式
date: 2018-04-12 10:12:51
categories: "设计模式"
tags: "策略模式"
---
>策略模式（Strategy）：它定义了算法家族，分别封装起来，让他们之间可以互换，  
此模式让算法的变化，不会影响到使用算法的客户。

```java
/**
 * @className: Strategy
 * @package: com.hh.designpattern.strategy
 * @describe: 抽象算法类
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:23
 **/
public abstract class Strategy {

    public abstract void algorithmInterface();

}

/**
 * @className: ConcreteStrategyA
 * @package: com.hh.designpattern.strategy
 * @describe: 具体算法A
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:28
 **/
public class ConcreteStrategyA extends Strategy {

    @Override
    public void algorithmInterface() {
        System.out.println("算法A实现");
    }

}

/**
 * @className: ConcreteStrategyA
 * @package: com.hh.designpattern.strategy
 * @describe: 具体算法B
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:28
 **/
public class ConcreteStrategyB extends Strategy {

    @Override
    public void algorithmInterface() {
        System.out.println("算法B实现");
    }

}

/**
 * @className: ConcreteStrategyA
 * @package: com.hh.designpattern.strategy
 * @describe: 具体算法C
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:28
 **/
public class ConcreteStrategyC extends Strategy {

    @Override
    public void algorithmInterface() {
        System.out.println("算法C实现");
    }

}

/**
 * @className: Context
 * @package: com.hh.designpattern.strategy
 * @describe: 上下文，维护对一个Strategy对象的引用
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:30
 **/
public class Context {

    private Strategy strategy;

    public Context(Strategy strategy) {
        this.strategy = strategy;
    }

    public void contextInterface() {
        strategy.algorithmInterface();
    }

}

/**
 * @className: Client
 * @package: com.hh.designpattern.strategy
 * @describe: 客户端
 * @auther: huanghai
 * @date: 2018/4/12 0012
 * @time: 上午 10:33
 **/
public class Client {

    public static void main(String[] args) {

        Context context;

        context = new Context(new ConcreteStrategyA());
        context.contextInterface();

        context = new Context(new ConcreteStrategyB());
        context.contextInterface();

        context = new Context(new ConcreteStrategyC());
        context.contextInterface();

    }

}
```

>策略模式优点：
* 策略模式是一种定义了一系列算法的方法，从概念上来看，所有的这些算法完成的都是  
相同的工作，只是实现不同，他们以相同的方式调用不同的算法，减少了各算法类与使用  
使用算法类之间的耦合
* 简化了单元测试，每个算法都有自己的类，可以通过自己的接口单独测试
