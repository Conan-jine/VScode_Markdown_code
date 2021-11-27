# 题目要求
1. 首先编写一个抽象类, 要求该类需要有如下3个抽象方法：
    >public abstract void f(int x);  
    public abstract void g(int x, inty);  
    public abstract double h(double x);  
2. 然后分别给出该类的3个子类. 要求: 在应用程序的主类中使用这些子类创建对象, 然后让他们的上转型对象调用方法：f()、g()和h().

# 题目要点
1. 上转型对象的使用
2. 抽象类的继承, 方法的实现

# 题目代码
``` Java
package work5;

abstract class A
{
	public abstract void f(int x);
	public abstract void g(int x, int y);
	public abstract double h(double x);
}

class A1 extends A
{
	@Override
	public void f(int x)
	{
		System.out.println(x);
	}

	@Override
	public void g(int x, int y)
	{
		System.out.println(x+y);
	}

	@Override
	public double h(double x)
	{
		return x*x;
	}
	
}

class A2 extends A
{
	@Override
	public void f(int x)
	{
		System.out.println(x);
	}

	@Override
	public void g(int x, int y)
	{
		System.out.println(Math.abs(x-y));
	}

	@Override
	public double h(double x)
	{
		return Math.sqrt(x);
	}
	
}

class A3 extends A
{
	@Override
	public void f(int x)
	{
		System.out.println(x);
	}

	@Override
	public void g(int x, int y)
	{
		System.out.println(Double.valueOf(x)/y);
	}

	@Override
	public double h(double x)
	{
		return 1/x;
	}
	
}

public class Work5_2
{
	public static void main(String[] args)
	{
		System.out.println("A类是A1, A2, A3的父亲, 用A类对象a调用子类方法");
		System.out.println("\n创建A1对象, 用它的上转型对象a调用它方法");
		A a = new A1();
		a.f(10);
		a.g(12, 20);
		System.out.println(a.h(100));
		
		System.out.println("\n创建A2对象, 用它的上转型对象b调用它方法");
		A b = new A2();
		b.f(10);
		b.g(12, 20);
		System.out.println(b.h(100));
		
		System.out.println("\n创建A3对象, 用它的上转型对象c调用它方法");
		A c = new A3();
		c.f(10);
		c.g(12, 20);
		System.out.println(c.h(100));
	}
}
```