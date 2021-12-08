## 题目要求

1. 键盘输入下面这首诗，并输出其每句的第一个字和最后一个字

   > 日暮苍山兰舟小
   >
   > 本无落霞缀清泉 
   >
   > 去年叶落缘分定 
   >
   > 死水微漾人却亡

   提示：定义二维字符数组char[][]，java使用unicode编码，一个汉字只占一个字符

## 题目要点

1. 数组的使用

## 题目代码

``` java
package work8;

import java.util.Scanner;

public class Work8_2
{
	public static void main(String[] args)
	{
		char[][] ts = new char[4][7];
		Scanner reader = new Scanner(System.in);
		String str;
		System.out.println("Input the poem:");
		for(int i=0; i<ts.length; i++)
		{
			str = reader.nextLine();
			ts[i] = str.toCharArray();
		}
		System.out.println("\nHide head:");
		for(int i=0; i<ts.length; i++)
		{
			for(int j=0; j<ts[i].length; j++)
			{
				if(j == 0)	System.out.print(ts[i][j]+" ");
			}
		}
		System.out.println("\nHide tail:");
		for(int i=0; i<ts.length; i++)
		{
			for(int j=0; j<ts[i].length; j++)
			{
				if(j == ts[i].length - 1)	System.out.print(ts[i][j]+" ");
			}
		}
		reader.close();
	}
}
```

