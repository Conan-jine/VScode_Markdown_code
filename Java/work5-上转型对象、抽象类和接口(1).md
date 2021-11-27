# 题目要求
1. 定义6个类, 编写一个Employee抽象类, 里面包含一个抽象方法方法public abstract double earnings();
2. 分别给出该类的三个子类, 重写抽象类的抽象方法, 编写一个Compay类实现对Employee 子类的管理, 实现求公司所有员工年薪方法
3. 最后编写一个主类, 实例化一个Compay对象, 并调用求年薪方法

# 题目要点
1. 使用上转型对象调用方法

# 题目结果
>Total annual salary of the company: 692000.0

# 题目代码
``` Java
package work5;

abstract class Employee
{
	public abstract double earnings();
}

class YearWorker extends Employee
{
	@Override
	public double earnings()
	{
		return 50000.0;
	}
}

class MonthWorker extends Employee
{
	@Override
	public double earnings()
	{
		return 2500.0;
	}
}

class WeekWorker extends Employee
{
	@Override
	public double earnings()
	{
		return 500.0;
	}
}

class Company
{
	Employee[] employee;
	double salaries = 0;
	Company(Employee[] employee)
	{
		this.employee = employee;
	}
	public double salariesPay()
	{
		salaries = 0;
		for(int i=0; i<employee.length; i++)
		{
			if(i%3 == 0)	salaries += employee[i].earnings()*52;
			else if(i%3 == 1)	salaries += employee[i].earnings()*12;
			else	salaries += employee[i].earnings();
		}
		return salaries;
	}
}

public class Work5_1
{
	public static void main(String[] args)
	{
		Employee[] employee = new Employee[20];
		for(int i=0; i<employee.length; i++)
		{
			if(i%3 == 0)	employee[i] = new WeekWorker();
			else if(i%3 == 1)	employee[i] = new MonthWorker();
			else if(i%3 == 2)	employee[i] = new YearWorker(); 
		}
		Company company = new Company(employee);
		System.out.println("Total annual salary of the company: "+company.salariesPay());
	}
}
```