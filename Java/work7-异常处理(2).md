## 题目要求

1. 声明2个Exception的异常子类：NoDigit类和NoLowerLetter类
2. 声明一个People类，里面有一个会抛出NoDigit异常的printDigit()方法和一个会抛出NoLowerLetter异常的printLetter()方法
3. 在主类中使用try-catch语句捕捉异常并输出

## 题目要点

1. throws 与 throw 的使用

## 题目代码

``` java
package work7;

@SuppressWarnings("serial")
class NoLowerLetter extends Exception
{
	public void print()
	{
		System.out.printf("%c", '#');
	}
}

@SuppressWarnings("serial")
class NoDigit extends Exception
{
	public void print()
	{
		System.out.printf("%c", '*');
	}
}

class People
{
	void printLetter(char c) throws NoLowerLetter
	{
		if( (c>='a' && c<='z') || (c>='A' && c<='Z') )	System.out.print(c);
		else
		{
			NoLowerLetter noLowerLetter = new NoLowerLetter();
			throw noLowerLetter;
		}
	}
	void printDigit(char c) throws NoDigit
	{
		if(c>='0' && c<='9')	System.out.print(c);
		else
		{
			NoDigit noDigit = new NoDigit();
			throw noDigit;
		}
	}
}

// ExceptionExample.java
public class Work7_2
{
	public static void main(String[] args)
	{
		People people = new People();
		for(int i=0; i<128; i++)
		{
			try
			{
				people.printLetter((char)i);
			}
			catch (NoLowerLetter e)
			{
				// TODO Auto-generated catch block
//				e.printStackTrace();
				System.out.print('#');
			}
		}
		System.out.println();
		for(int i=0; i<128; i++)
		{
			try
			{
				people.printDigit((char)i);
			}
			catch (NoDigit e)
			{
				// TODO Auto-generated catch block
//				e.printStackTrace();
				System.out.print('*');
			}
		}
	}
}
```

