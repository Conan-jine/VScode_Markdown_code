## 题目要求

1. 有一个类A, 有两个成员变量, 一个为实例变量float a, 另一个为静态变量float b
2. 有2个set方法来实现对成员变量的赋值
3. 有2个get方法实现对成员变量数值的读取
4. 有2个input方法实现对成员信息的打印
5. 定义一个主类, 使用类A的静态成员, 静态方法
6. 实例化类A的对象, 通过对象调用类A的方法

## 程序预期打印结果

>100.0  
200.0  
900.0  
300.0  
900.0  

## 程序要点

1. 使用 static 修饰的方法和变量, 可使用类名直接调用

## 程序代码

``` Java
package work3;

class A
{
	float a;
	static float b;
	
	void setA(float a)
	{
		this.a = a;
	}
	
	void setB(float b)
	{
		A.b = b;
	}
	
	float getA()
	{
		return this.a;
	}
	
	float getB()
	{
		return A.b;
	}
	
	void inputA()
	{
		System.out.println(this.a);
	}
	
	static void inputB()
	{
		System.out.println(A.b);
	}
}

public class work3_1
{
	public static void  main(String[] args)
	{
		// 通过类名操作变量b, 赋值100;
		A.b = 100;
		// 通过类名调用方法 inputB()
		A.inputB();
		
		A cat = new A();
		A dog = new A();
		
		cat.setA(200);
		cat.setB(400);
		
		dog.setA(300);
		dog.setB(900);
		
		cat.inputA();
		cat.inputB();
		
		dog.inputA();
		dog.inputB();
	}
}
```