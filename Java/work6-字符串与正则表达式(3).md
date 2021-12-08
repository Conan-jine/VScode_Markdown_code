## 题目要求

1. 输入一个字符串，根据中国身份证号和简单电子邮箱的特点各自设计一个正则表达式， 判断输入的字符串是否匹配对应正则表达式，显示身份证号和邮箱是否合法

## 题目要点

1. 正则表达式的运用(目前也只是了解了大概)
2. 设计正则表达式大概就是将原来的字符串表示为单特征的多个字符串组合，正则表达式是单特征的组合

## 题目代码

``` java
package work6;

import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Work6_3
{
	public static void main(String[] args)
	{
		Scanner s = new Scanner(System.in);
		System.out.println("Please input your ID number:");
		String temp = s.nextLine();
		Pattern p1 = Pattern.compile("\\w{18}");
		Matcher m = p1.matcher(temp);
		if(m.matches())	System.out.println("ID number is legal.");
		else	System.out.println("ID number is wrong!");
		
		System.out.println("Please input your email:");
		temp = s.nextLine();
		Pattern p2 = Pattern.compile("\\w+@{1}\\w+.+\\w+");
		m = p2.matcher(temp);
		if(m.matches())	System.out.println("Email format is correct.");
		else	System.out.println("Email format is error");
		s.close();
	}
}
```

