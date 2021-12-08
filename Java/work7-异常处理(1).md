## 题目要求

1. 使用try-catch语句捕分别捕捉输入格式异常和数组越界异常异常，并输出异常信息

## 题目要点

无

## 题目代码

``` java
package work7;

import java.util.Scanner;

public class Work7_1
{
	public static void main(String[] args)
	{
		@SuppressWarnings("unused")
		double a;
		int[] array = new int[2];
		Scanner scanner = new Scanner(System.in);
		try
		{
			System.out.println("Input number:");
			a = scanner.nextDouble();
		}
		catch(Exception e)
		{
			System.out.println("Error format of the numebr!");
			e.printStackTrace();
		}
		
		try
		{
			array[2] = 8;
		}
		catch(Exception e)
		{
			System.out.println("Array overflow exception!");
			e.printStackTrace();
		}
		scanner.close();
	}
}
```

