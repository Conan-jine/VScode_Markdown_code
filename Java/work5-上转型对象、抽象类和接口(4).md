## 题目要求

1. 定义5个类以及一个接口, 编写一个ComputeSales(计算销售)接口，里面包含一个方法double Sales( ); 默认为 public abstract 修饰的方法
2. 三个电器类分别使用ComputeSale接口并实现接口的方法, 编写一个Shop类通过接口实现对三电器类的销售额管理, 实现求一天销售总额方法
3. 最后编写一个主类, 实例化一个接口数组, 假设每天最多可以卖出20个电器, 并调用求销售总额方法求出电器销售总额

## 题目要点

1. 数组各项的实例化

## 题目代码

``` Java
package work5;

interface ComputerSales
{
	double Sales();
}

class Television implements ComputerSales
{
	@Override
	public double Sales()
	{
		return 2300.0;
	}
}

class Computer implements ComputerSales
{
	@Override
	public double Sales()
	{
		return 4500.0;
	}
}

class Mobile implements ComputerSales
{
	@Override
	public double Sales()
	{
		return 1200.0;
	}
}

class Shop
{
	ComputerSales[] goods;
	double totalSales = 0;
	Shop(ComputerSales[] goods)
	{
		this.goods = goods;
	}
	public double giveTotalSales(int n)
	{
		totalSales = 0;
		for(int i=0; i<n; i++)	totalSales += goods[i].Sales();
		return totalSales;
	}
}

public class Work5_4
{
	public static void main(String[] args)
	{
		ComputerSales[] goods = new ComputerSales[20];
		int temp;
		int total;
		total = (int)(Math.random()*21);
		for(int i=0; i<total; i++)
		{
			temp = (int)(Math.random()*3);
			if(temp == 0)
			{
				goods[i] = new Television();
				System.out.println("商店销售出一台电视机");
			}
			else if(temp == 1)
			{
				goods[i] = new Computer();
				System.out.println("商店销售出一台电脑");
			}
			else if(temp == 2)
			{
				goods[i] = new Mobile();
				System.out.println("商店销售出一台手机");
			}
		}
		Shop shop = new Shop(goods);
		System.out.println("今天商店销售电器总数为: "+total);
		System.out.println("今天商店销售额: "+shop.giveTotalSales(total));
	}
}
```