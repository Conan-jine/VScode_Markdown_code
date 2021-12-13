## 题目要求

1. 自定义泛型并使用

2. 编写1个随机生成花色的Color类，1个随机生成点数的Point类，以及1个泛型类Poker<C,P>

3. 在主类中调用泛型类随机生成5张扑克牌并打印显示。

   > 提示：在Color类和Point类中重写Object类的toString（）方法，该方法分别返回一个随机花色和随机点数。泛型类Poker<C,P>作用就是将C、P两个的toString（）组合起来即可。

## 题目要点

1. 泛型对象的初始化

## 题目代码

``` java
package work10;

import java.util.Random;

class Color
{
	@Override
	public String toString()
	{
		String str;
		Random r = new Random();
		int i = r.nextInt(4) + 1; // 随机生成1到4的整数

		switch(i)// 选择初始化花色
		{
			case 1:
				str = "黑桃";
				break;
			case 2:
				str = "红心";
				break;
			case 3:
				str = "梅花";
				break;
			default:
				str = "方片";
				break;
		}
//		System.out.println(str);
		return str;
	}
}

class Point
{
	@Override
	public String toString()
	{
		String str;
		Random r = new Random();
		int i = r.nextInt(13) + 1;// 随机生成1到13的整数

		switch(i)// 选择初始化点数
		{
			case 1:
				str = "A";
				break;
			case 11:
				str = "J";
				break;
			case 12:
				str = "Q";
				break;
			case 13:
				str = "K";
				break;
			default:
				str = Integer.toString(i);
				break;
		}
//		System.out.println(str);
		return str;
	}
}

class Poker<C, P>
{// 定义泛型类Poker
	C c;
	P p;

	Poker(C c, P p)
	{
		this.c = c;
		this.p = p;
	}

	public String gets()
	{
		return c.toString() + p.toString();// 返回C和P的两个toString()组合
	}

}

public class Work10_1
{
	public static void main(String[] args)
	{
		Color color = new Color();
		Point point = new Point();
		Poker<Color, Point> poker = new Poker<Color, Point>(color, point);
		for(int i = 1; i <= 5; i++)
			System.out.println("随机生成：" + poker.gets());
	}

}
```

