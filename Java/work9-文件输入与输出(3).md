## 题目要求

1. 将已经存在的source.txt文件加密后存入另一个文本文件encode.txt,再将encode.txt解密,还原到decode.txt中(使用字符流)

## 题目要点

1. FileReader 与 FileWriter 的使用
2. 加密与解密手法
3. 文件自备

## 题目代码

``` java
package work9;

import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class Work9_3
{
	public static void main(String[] args)
	{
		File source = new File("D:/ch8/source.txt");
		File encode = new File("D:/ch8/encode.txt");
		File decode = new File("D:/ch8/decode.txt");
		char[] b = new char[100];
		try
		{
			FileReader in = new FileReader(source);
			FileWriter out = new FileWriter(encode);
			int n = 1;
			while((n = in.read(b)) != -1)
			{
				for(int i=0; i<n; i++)	b[i] = (char)(b[i]^'a');
				out.write(b);
			}
			in.close();
			out.close();
			
			in = new FileReader(encode);
			System.out.println("Encode file:");
			while((n = in.read(b)) != -1)
			{
				System.out.println(b);
			}
			in.close();
			
			in = new FileReader(encode);
			out = new FileWriter(decode);
			n = 1;
			while((n = in.read(b)) != -1)
			{
				for(int i=0; i<n; i++)	b[i]=(char)(b[i]^'a');
				out.write(b);
			}
			in.close();
			out.close();
			
			System.out.println("Decode file:");
			in = new FileReader(decode);
			while((n = in.read(b)) != -1)
			{
				System.out.println(b);
			}
			in.close();
		}
		catch(IOException e)
		{
			System.out.println(e);
		}
	}
}
```

