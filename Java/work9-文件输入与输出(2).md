## 题目要求

1. 已存在的文件source.txt里有一段文字,现键盘上输入(使用缓冲流实现)一个文件名比如:copy.txt
2. 创建这个文件,并将source.txt的内容复制到copy.txt中(使用字节流实现)

## 题目要点

1. FileInputStream 类
2. FileOutputStream 类
3. BufferedInputStream 类
4. BufferedOutputStream 类
5. FileInputStream 与 BufferedInputStream 的串联
6. FileOutputStream 与 BufferedOutputStream 的串联

## 题目代码

``` java
package work9;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStreamReader;

public class Work9_2
{
	public static void main(String[] args)
	{
		FileInputStream fis = null;
		FileOutputStream fos = null;
		BufferedInputStream bis = null;
		BufferedOutputStream bos = null;
		int c;
		try
		{
			System.out.println("Input file name:");
			BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
			String fname = in.readLine();
			
			fis = new FileInputStream("D:/ch8/source.txt");
			bis = new BufferedInputStream(fis);
			
			fos = new FileOutputStream("D:/ch8/"+fname);
			bos = new BufferedOutputStream(fos);
			
			while((c = bis.read() )!= -1)
			{
				bos.write(c);
			}
			bos.flush();
			System.out.println("File copy done.");
		}
		catch(IOException e)
		{
			System.out.println(e);
		}
		finally
		{
			try
			{
				if(fis != null)	fis.close();
				if(fos != null)	fos.close();
				if(bis != null)	bis.close();
				if(bos != null)	bos.close();
			}
			catch(IOException e1)
			{
				System.out.println(e1);
			}
		}
	}
}
```

