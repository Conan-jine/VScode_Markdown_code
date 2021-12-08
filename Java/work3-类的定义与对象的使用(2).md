## 题目要求

1. 定义设计一个Trangle(三角形)类, 该类放在tom.jiafei包中, 要求包含4个成员变量, 三条边sideA, sideB, sideC, 一个布尔值bool(判断是否成为三角形)包含构造函数, 求三角形面积的方法getArea和重新设置三角形三条边的方法setLength
2. 定义个主类, 创建Trangle类的对象, 调用方法对输入的三条边进行面积计算

## 题目难点

1. 判断三边是否构成三角形
2. 计算三角形面积

## 实现代码

``` Java
package work3;

import java.util.Scanner;

class Trangle
{
	double sideA, sideB, sideC;
	boolean bool;
	
	// 有参构造函数, 赋值三条边
	Trangle(double a, double b, double c)
	{
		this.sideA = a;
		this.sideB = b;
		this.sideC = c;
		judgeTrangle();
	}
	
	// 判断三条边是否构成三角形
	void judgeTrangle()
	{
		bool = true;
		if(sideA + sideB <= sideC)	bool = false;
		if(sideB + sideC <= sideA)	bool = false;
		if(sideA + sideC <= sideB)	bool = false;
	}
	
	// 计算三角形面积
	void getArea()
	{
		judgeTrangle();
		if(this.bool == false)	System.out.println("Not a trangle, can not calculate area.");
		else
		{
			System.out.println("Is a trangle, the area can be calculate");
			double p = (sideA + sideB + sideC)/2.0;
			double Area = Math.sqrt(p*(p-sideA)*(p-sideC)*(p-sideB));
			System.out.println("Area is: "+Area);
		}
			
	}
	
	// 设置三边长度
	void setLength()
	{
		double a, b, c;
		Scanner reader = new Scanner(System.in);
		System.out.println("Reset three side:");
		a = reader.nextDouble();
		b = reader.nextDouble();
		c = reader.nextDouble();
		this.sideA = a;
		this.sideB = b;
		this.sideC = c;
		reader.close();
	}
}

public class work3_2
{
	public static void main(String[] args)
	{
		double a, b, c;
		Scanner reader = new Scanner(System.in);
		System.out.println("Input three side: ");
		a = reader.nextDouble();
		b = reader.nextDouble();
		c = reader.nextDouble();
		Trangle one = new Trangle(a, b, c);
		one.getArea();
		one.setLength();
		one.getArea();
		reader.close();
	}
}
```