# 题目要求
1. 一个person类作为父类, 该类中包含成员变量weight, height, 实例方法speakHello()averageHeight() 和 averageWeight()
2. 分别编写ChinaPeople和AmericanPeople两个类继承People类, 分别根据提示重写它的三个方法, 并在ChinaPeople类中添加chinaGongfu()方法, 在AmericanPeople 类中添加americanBoxing()方法
3. 定义一个主类Example, 在主类中创建ChinaPeople和AmericanPeople两个类的对象并调用他们的方法

# 知识要点
1. extends 的使用
2. @Override 的使用

# 题目代码
``` Java
package work4;

class People
{
	protected double weight, height;
	
	public void speakHello()
	{
		System.out.println("yayawawa");
	}
	
	public void averageHeight()
	{
		height = 173;
		System.out.println("average height: "+height);
	}
	
	public void averageWeight()
	{
		weight = 70;
		System.out.println("average weight: "+weight);
	}
}

class ChinaPeople extends People
{
	// 重写
	@Override
	public void speakHello()
	{
		System.out.println("你好, 吃饭了吗?");
	}
	
	@Override
	public void averageHeight()
	{
		height = 168.78;
		System.out.println("中国人的平均身高: "+height+"厘米");
	}
	
	@Override
	public void averageWeight()
	{
		weight = 65.0;
		System.out.println("中国人的平均体重: "+weight+"公斤");
	}
	
	public void chinaGongfu()
	{
		System.out.println("中国武术: 坐如钟, 站如松, 睡如弓");
	}
}

class AmericanPeople extends People
{
	@Override
	public void speakHello()
	{
		System.out.println("How do you do?");
	}
	
	@Override
	public void averageHeight()
	{
		System.out.println("American Average height: 172.0cm");
	}
	
	@Override
	public void averageWeight()
	{
		System.out.println("American Average weight: 80.23kg");
	}
	
	public void americanBoxing()
	{
		System.out.println("美国拳击: 直拳, 勾拳");
	}
}

public class Example_1
{
	public static void main(String[] args)
	{
		ChinaPeople one = new ChinaPeople();
		AmericanPeople two = new AmericanPeople();
		one.speakHello();
		two.speakHello();
		one.averageHeight();
		two.averageHeight();
		one.averageWeight();
		two.averageWeight();
		one.chinaGongfu();
		two.americanBoxing();
	}
}
```