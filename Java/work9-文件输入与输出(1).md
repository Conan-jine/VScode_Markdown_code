## 题目要求

1. 如果目录d:\ch8存在，则显示该目录下的所有文件的名字和大小，显示该目录下的所有txt文件的名字和大小
2. 否则创建该目录，并创建一个4个txt文件和4个dat文件

## 题目要点

1. 使用 File 类创建文件
2. 使用 File 类创建目录
3. 重写 accept 函数

## 题目代码

``` java
package work9;

import java.io.File;
import java.io.FilenameFilter;
import java.io.IOException;

class FileAccept implements FilenameFilter
{
	String str = null;
	FileAccept(String s)
	{
		str="."+s;
	}
	
	@Override
	public boolean accept(File dir, String name)
	{
		return new File(dir, name).isDirectory() || name.endsWith(str);
	}
}

public class Work9_1
{
	public static void main(String[] args) throws IOException
	{
		File dir = new File("D:\\ch8");
		if(!dir.exists())
		{
			dir.mkdir();
			File[] f = new File[8];
			for(int i=0; i<8; i++)
			{
				if(i%2 == 1)	f[i] = new File(dir, i+".txt");
				else	f[i] = new File(dir, i+".dat");
				if(!f[i].exists())	f[i].createNewFile();
			}
			System.out.println("Successfully created eight files.");
			
		}
		else
		{
			File[] list = dir.listFiles();
			System.out.println("The files in the "+dir.getPath()+" are:");
			for(int i=0; i<list.length; i++)
				System.out.println(list[i].getName()+" "+list[i].length());
			System.out.println("The txtFiles in the "+dir.getPath()+" are:");
			FileAccept accept = new FileAccept("txt");
			list = dir.listFiles(accept);
			for(int i=0; i<list.length; i++)
				System.out.println(list[i].getName()+" "+list[i].length());
		}
	}
}
```

