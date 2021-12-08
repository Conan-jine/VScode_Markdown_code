## 题目要求

1. 定义一个StringBuffer,对其进行多种操作

## 题目要点

1. StringBuffer 类的 append、replace、insert、delete等函数

## 题目代码

``` Java
package work6;

// StringBufferExample.java
public class Work6_2
{
	public static void main(String[] args)
	{
		StringBuffer str = new StringBuffer("ABCDEFG");
		str.append("123456789");
		System.out.println(str);
		str.replace(1, 2, "b");
		System.out.println(str);
		str.insert(str.indexOf("123456789"), "Game");
		System.out.println(str);
		
		int index = str.indexOf("1");
		str.delete(index, index+4);
		int n = str.length();
		str.replace(n-3, n, "七八九");
		System.out.println(str);
	}
}
```



