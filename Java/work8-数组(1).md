## 题目要求

1. 随机生成20个100以内的整数，将他们存到一维数组A中
2. 将数组A中的后10个数复制到数组B中，并将数组B中的数据进行升序排序
3. 键盘输入一个整数，在数组B中使用二叉查找法查找这个数，如找到则输出其下标，否则输出找不到

## 题目要点

1. Arrays 当中 sort 的使用
2. System 当中 arraycopy 的使用

## 题目代码

``` java
package work8;

import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class Work8_1
{
	public static void main(String[] args)
	{
		Random r = new Random();
		int[] A = new int[20];
		int[] B = new int[10];
		
		System.out.println("Randomly generate 20 integers put into A:");
		for(int i=0; i<20; i++)
		{
			A[i] = r.nextInt(100);
			System.out.print(A[i]+" ");
		}
		System.out.println();
		System.out.println("Assign the last 10 numbers of array A to B:");
		System.arraycopy(A, 10, B, 0, 10);
		for(int i=0; i<B.length; i++)	System.out.print(B[i]+" ");
		System.out.println();
		
		System.out.println("Sort array B in ascending order:");
		Arrays.sort(B);
		for(int i=0; i<B.length; i++)	System.out.print(B[i]+" ");
		System.out.println();
		
		Scanner reader = new Scanner(System.in);
		System.out.println("Input the number need to find:");
		int num = reader.nextInt();
		
		System.out.println("Use binary search to find in array B:");
		int index = Arrays.binarySearch(B, num);
		if(index > -1)	System.out.println("The index of "+num+" is: "+index);
		else System.out.println(num+" is not in B");
		reader.close();
	}
}
```

