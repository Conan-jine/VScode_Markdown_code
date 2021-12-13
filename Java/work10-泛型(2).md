## 题目要求

1. ArrayList的使用

2. 编写1个Student类，有1个name成员变量。键盘输入4个人名，并初始化4个学生实例

3. 在主类中定义一个ArrayList< Student >泛型,对ArrayList进行多种操作,包括添加、移除、判断元素是否存在列表中和查找序号、输出列表长度以及遍历输出等。

   > 提示：必须在Student类中重写equals方法，以此保证只要名字相等，则认为是同一个人

## 题目要点

1. 如何重写equals方法
2. ArrayList泛型对象的定义与使用

## 题目代码

```java
package work10;

import java.util.ArrayList;
import java.util.Scanner;

class Student
{
	String name;

	Student(String name){ this.name = name; } // 构造方法

	@Override
	public boolean equals(Object obj)
	{
		if(obj instanceof Student)
		{
			Student stu = (Student)obj;
			return name.equalsIgnoreCase(stu.name);
		}
		else	return false;
	}
}

public class Work10_2
{
	public static void main(String[] args)
	{
		 Scanner reader = new Scanner(System.in);
		 Student[] stu = new Student[4];
		 ArrayList<Student> list = new ArrayList<Student>();
		 //定义 ArrayList泛型，每个元素是1个学生。
		 
		 System.out.println("输入4个学生姓名：");
		 // 初始化4个学生，并将他们添加进ArrayList
		 for(int i=0;i<4;i++)
		 {
			 stu[i] = new Student(reader.nextLine());
			 list.add(stu[i]);
		 }
		 
		 System.out.println("列表中还有" + list.size() + "个学生：");
		 
		 for (int i=0; i<list.size(); i++)
             System.out.println("第"+i+"个学生: "+list.get(i).name);
		 
		//键盘输入一个学生姓名,判断该学生是否在列表中，如存在，则输出其在列表中的下标，然后将它从列表中移除。
		
		 System.out.println("输入要查找的人的姓名：");
		 Student s = new Student(reader.nextLine()); 
		 if(list.contains(s))
		 { 
			 
			 System.out.println("找到"+s.name+"，下标为"+list.indexOf(s));//输出下标
			 list.remove(list.indexOf(s));    //从列表中移除该学生
			 
			 System.out.println("删除"+s.name+"后,还有"+list.size()+"个学生：");
			 
			 for (int i=0; i<list.size(); i++)
	             System.out.println("第"+i+"个学生: "+list.get(i).name);
		 }
		 else	System.out.println("列表中找不到"+s.name);  //如不存在则输出找不到。
		 reader.close();
	}

}
```

