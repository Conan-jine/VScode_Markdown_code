## 题目要求

1. 从键盘输入的一堆字符串乱码中找出数字
2. 并将它们相加求和

## 题目要点

1. Scanner 定向至字符串
2. Scanner 的 useDelimiter 函数

## 题目代码

``` java
package work6;

import java.util.Scanner;

public class Work6_4
{
	public static void main(String[] args)
	{
		System.out.println("Input string:");
		Scanner reader = new Scanner(System.in);
		String str = reader.nextLine();
		
		Scanner scanner = new Scanner(str);
		double sum = 0;
		scanner.useDelimiter("[^01234567890.]+");
		while(scanner.hasNextDouble())	sum += scanner.nextDouble();
		System.out.println("The sum of all numbers in the string: "+sum);
		reader.close();
		scanner.close();
	}
}
```

