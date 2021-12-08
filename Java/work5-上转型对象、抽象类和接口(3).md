## 题目要求

1. 编写一个类, 要求该类实现一个接口, 该接口有如下3个抽象方法:
    >public abstract void f(int x);
    public abstract void g(int x, inty);
    public abstract double h(double x);
2. 要求: 在应用程序的主类中使用该类创建对象, 并使用接口回调来调用方法: f()、g()和h().

## 题目要点

1. 接口的实现
2. 接口的使用

## 题目代码

``` Java
package work5;

interface AA
{
	public abstract void f(int x);
	public abstract void g(int x, int y);
	public abstract double h(double x);
}

class AA1 implements AA
{
	@Override
	public void f(int x)
	{
		System.out.println("调用f方法, 传入整数为: "+x);
	}

	@Override
	public void g(int x, int y)
	{
		System.out.println("调用g方法, 传入两个整数之和为: "+(x+y));
	}

	@Override
	public double h(double x)
	{
		return x*x;
	}
	
}

public class Work5_3
{
	public static void main(String[] args)
	{
		AA a = new AA1();
		a.f(10);
		a.g(12, 20);
		System.out.println("调用h方法, 传入整数的平方为: "+a.h(100));
	}
}
```