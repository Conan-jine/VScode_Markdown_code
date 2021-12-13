## 题目要求

1. 随机布雷。编写1个Block类，有2个成员变量name和boo，以及若干个方法
2. 定义1个LinkList< Block >泛型和1个8*8的Block方阵，将方阵的坐标存储到LinkList泛型中，并将改写随机生成的地雷坐标的名字
3. 在主类中调用泛型并打印出随机布雷方阵。

## 题目要点

1. LinkedList 对象的定义与所含有函数的使用

## 题目代码

``` java
package work10;

import java.util.LinkedList;

class Block
{
	String name;
	boolean boo = false;

	public void setName(String name)
	{
		this.name = name;
	}

	public String getName()
	{
		return name;
	}

	boolean isMine()
	{
		return boo;
	}

	public void setBoolean(boolean boo)
	{
		this.boo = boo;
	}
}

public class Work10_3
{
	public static void main(String args[])
	{
		int mine = 25;
		Block block[][] = new Block[8][8];
		for (int i = 0; i < 8; i++)
		{
			for (int j = 0; j < 8; j++)
			{
				block[i][j] = new Block();
			}
		}
		LinkedList<Block> list = new LinkedList<Block>();
		for (int i = 0; i < 8; i++)
		{
			for (int j = 0; j < 8; j++)
			{
				list.add(block[i][j]);
			}
		}
		while (mine >= 0)
		{
			int size = list.size();
			int randomIndex = (int) (Math.random() * size);
			Block b = list.get(randomIndex);
			b.setName("@");
			b.setBoolean(true);
			list.remove(randomIndex);
			mine--;
		}
		for (int i = 0; i < 8; i++)
		{
			for (int j = 0; j < 8; j++)
			{
				if (block[i][j].boo == true) continue;
				else
				{
					int mineNumber = 0; // 计算非雷坐标的周围存在的地雷个数，并将个数设置为name
					for (int k = Math.max(i - 1, 0); k <= Math.min(i + 1, 7); k++)
					{
						for (int t = Math.max(j - 1, 0); t <= Math.min(j + 1, 7); t++)
						{
							if (block[k][t].boo == true) // 判断block[k][t]是否是地雷
								mineNumber++;
						}
					}
					block[i][j].setName("" + mineNumber);
				}
			}
		}
		for (int i = 0; i < 8; i++)
		{
			for (int j = 0; j < 8; j++)
			{
				System.out.printf("%2s", block[i][j].getName());
			}
			System.out.printf("%n");
		}
	}
}
```

