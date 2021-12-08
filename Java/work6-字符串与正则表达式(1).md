## 题目要求

1. 编写一个Java 应用程序，判断两个字符串是否相同
2. 判断字符串的前缀、后缀是否与某个字符串相同
3. 按字典比较两个字符串的大小关系
4. 进行字符串检索，创建子字符串
5. 将数字型字符串转化为数字，将字符串存放到数组中，用字符数组创建字符串



## 题目要点

1. String 类的 equals 函数
2. 字符串前缀后缀函数 startWith 和 endWith
3. 字典序比较函数 compareTo
4. 字符串检索函数 lastIndexOf
5. 字符串截取子串函数 substring
6. String 转 char[] 函数 toCharArray



## 题目代码

``` Java
package work6;

public class Work6_1
{
	public static void main(String[] args)
	{
		String s1 = new String("You are a student");
		String s2 = new String("How are you");
		if(s1.equals(s2))	System.out.println("s1 与 s2 相同");
		else	System.out.println("s1 与 s2 不相同");
		
		String s3 = new String("22030219851022024");
		if(s3.startsWith("220302"))	System.out.println("吉林省的身份证");
		
		String s4 = new String("You");
		String s5 = new String("Me");
		if(s4.compareTo(s5)>0)	System.out.println("s4 bigger than s5");
		else System.out.println("s5 bigger than s4");
		
		int position = 0;
		String path = "/Java-demo/work6/Work6_1.java";
		position = path.lastIndexOf("/");
		System.out.println("/Java-demo/work6/Work6_1.java last index of '/' is "+position);
		
		String filename = path.substring(position+1);
		System.out.println("/Java-demo/work6/Work6_1.java include "+filename);
		
		String s6 = new String("100");
		String s7 = new String("123.678");
		int n1 = Integer.parseInt(s6);
		double n2 = Double.parseDouble(s7);
		double n = n1 + n2;
		System.out.println(n);
		
		String s8 = new String("ABCDEF");
		char a[] = s8.toCharArray();
		for(int i=a.length-1; i>=0; i--)	System.out.printf("%3c", a[i]);
	}
}
```



