## 题目要求

1. 键盘输入5个整数,并将它们写入到一个名为tom.dat的文件中,然后按相反的顺序读出这些数据
2. 修改文件中第3个数，将其改为0

## 题目要点

1. RandomAccessFile 当中 seek 的使用

## 题目代码

``` java
package work9;

import java.io.IOException;
import java.io.RandomAccessFile;
import java.util.Scanner;

public class Work9_4
{
	public static void main(String[] args)
	{
		RandomAccessFile rf = null;
		Scanner reader = new Scanner(System.in);
		int num;
		try
		{
			rf = new RandomAccessFile("D:/ch8/tom.dat","rw");
		}
		catch(Exception e)
		{
			
		}
		
		try
		{
			for(int i=0; i<5; i++)
			{
				num = reader.nextInt();
				rf.write(num);
			}
			for(int i=4; i>=0; i--)
			{
				rf.seek(i);
				num = rf.read();
				System.out.print(num+" ");
			}
			
			System.out.println();
			rf.seek(2);
			rf.write(0);
			for(int i=0; i<5; i++)
			{
				rf.seek(i);
				num = rf.read();
				System.out.print(num+" ");
			}
			rf.close();
			reader.close();
		}
		catch(IOException e)
		{
			
		}
	}
}
```

