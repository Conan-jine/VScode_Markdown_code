## 程序要求

1. 输出特定半径长的圆形的面积
2. 输出特定长和宽的矩形的面积

## 程序难点

1. 打印字符串和数字的组合, 使用 + 号
   

## 程序代码

```Java
package work1;

public class Area
{
	static final double PI = 3.1415;
	
	public static void main(String[] args)
	{
		double r, CircleArea, height, weight, MatrixArea;
		r = 3;
		height = 4;
		weight = 5;
		CircleArea = PI * r * r;
		MatrixArea = height * weight;
		System.out.println("Circle Area = " + CircleArea);
		System.out.println("Matrix Area = " + MatrixArea);
	}
	
}
```