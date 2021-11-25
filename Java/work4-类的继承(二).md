# 题目要求
1. 编写一个类，该类有一个方法f, 要求该方法返回a和b的最大公约数
2. 然后编写一个该类的子类, 要求子类重新写方法, 而其重写方法将返回两个整数的最小公倍3. 重写的方法的方法体中首先调用被隐藏的方法返回a和b的最大公约数m, 然后将(a*b)/m返回
3. 在应用程序的主类中分别使用父类和子类创建的对象, 并分别调用方法f计算两个正整数的最大公约数和最小公倍数

# 题目难点
1. 子类调用父类方法
   >使用super关键字
2. 求最大公约数的方法

# 题目代码
``` Java
package work4;

import java.util.Scanner;

class A
{
	public int f(int m, int n)
	{
		int temp;
		if(m <= n)
		{
			temp = m;
			m = n;
			n = temp;
		}
		temp = m % n;
		while(temp != 0)
		{
			m = n;
			n = temp;
			temp = m % n;
		}
		return n;
	}
}

class B extends A
{
	@Override
	public int f(int m, int n)
	{
		return m * n / super.f(m, n);
	}
}

public class Example_2
{
	public static void main(String[] args)
	{
		A a = new A();
		B b = new B();
		int m, n;
		Scanner reader = new Scanner(System.in);
		System.out.println("Input the first integer:");
		m = reader.nextInt();
		System.out.println("Input the second intefer:");
		n = reader.nextInt();
		System.out.println("Greatest common divisor is: "+a.f(m, n));
		System.out.println("Least common multiple is: "+b.f(m, n));
		reader.close();
	}
}
```