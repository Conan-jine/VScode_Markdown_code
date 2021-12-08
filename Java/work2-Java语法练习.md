## 题目要求

1. 定义重力加速度常量G, 值为9.8, 忽略空气阻力等因素, 计算从物体100米高度下落到地面需要的时间
2. 定义整数变量m和n, 计算m~n之间能被3和7同时整除的整数之和(使用命令行参数的形式赋予m和n的值)
3. 定义整数变量m和n, 计算m~n之间能被3和7同时整除的整数之和(使用scanner类赋予m和n的值)

## 题目难点

1. 获取命令行参数
   
   >命令行参数存于 String 类型的 args 数组中
2. 因命令行参数为 String 类型, 需要使用类型转换, 转换成 int
   
   >函数 Integer.parseInt( String类型参数 ) , 返回值为 int 型
3. 获取键盘输入
   
   >使用 Scanner 类 生产具体实例, 读取 System.in 的内容
4. 获取特定类型的输入值
   
   >使用 Scanner 类中的 nextInt() nextString() 等相关函数

## 题目代码

``` Java
package work2;

import java.util.Scanner;

public class Grammar
{
	// 定义重力加速度常量
	static final double G = 9.8;
	public static void main(String[] args)
	{
		int m, n, fallDistance = 100;
		
		// 计算下落100米所需时间
		calculateFallTime(fallDistance);
		
		// 获取命令行输入的值
		if(args.length != 0)
		{
			m = Integer.parseInt(args[0]);
			n = Integer.parseInt(args[1]);
			System.out.println("The command line input result is:");
			calculateSumBetween(m, n);
		}
		
		// 获取键盘输入的值
		Scanner reader = new Scanner(System.in);
		System.out.println("Please input n, m, split with spaces:");
		m = reader.nextInt();
		n = reader.nextInt();
		calculateSumBetween(m, n);
		reader.close();
	}
	
	// 计算下落时间函数
	public static void calculateFallTime(int fallDistance)
	{
		double t;
		t = Math.sqrt(fallDistance * 2 / G);
		System.out.println("t = "+t);
	}
	
	// 计算两数之间符合条件的数之和
	public static void calculateSumBetween(int m, int n)
	{
		int sum = 0;
		for(int i = m; i <= n; i++)
		{
			if(i % 3 == 0 && i % 7 == 0)	sum += i;
		}
		System.out.println("sum of "+m+" ~ "+n+" = "+sum);
	}
}
```