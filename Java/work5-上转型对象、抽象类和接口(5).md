## 题目要求

1. 实现系统定义好的接口, 接口回调

## 代码解释

1. 在定时器启动后, 即t.start()语句执行后, 程序将会弹出一个消息对话框,并等待用户点击ok按钮来终止程序的执行. 在程序等待用户操作的同时, 每隔10秒显示一次当前时间.
2. 运行这个程序一定要有一些耐心, 程序启动后, 将会立即显示一个消息对话框, 10秒钟后, 第一条显示信息才会显示出来

## 题目代码

``` Java
package work5;

import java.util.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.Timer;

class TimePrinter implements ActionListener
{
	public void actionPerformed(ActionEvent event)
	{
		Date now = new Date();
		System.out.println("At the tone, the time is: "+now);
		Toolkit.getDefaultToolkit().beep();
	}
}

public class Work5_5 // TimerTest
{
	public static void main(String[] args)
	{
		ActionListener listener = new TimePrinter();
		Timer t = new Timer(10000, listener);
		t.start();
		
		JOptionPane.showMessageDialog(null, "Quit program?");
		System.exit(0);
	}

}
```