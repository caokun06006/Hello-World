# Hello-World
First Repository
package com.ck.test;

import java.io.File;
import java.util.Scanner;

public class Test0204 {
	/*
	 * 从键盘接收一个文件夹路径,把文件夹中的所有文件以及文件夹的名字按层级打印, 例如:
		aaa是文件夹,里面有bbb.txt,ccc.txt,ddd.txt这些文件,有eee这样的文件夹,eee中有fff.txt和ggg.txt,打印出层级来
		aaa
			bbb.txt
			ccc.txt
			ddd.txt
		
			eee
				fff.txt
				ggg.txt
	 */
	public static void main(String[] args) {
		//int level = 0;
		print2(getFile(),0);
	}
	
	public static File getFile() {
		Scanner sc = new Scanner(System.in);
		System.out.println("请录入文件夹路径");
		while(true) {
			String len = sc.nextLine();
			File file = new File(len);
			if (!file.exists()) {
				System.out.println("请重新录入");
			}else if(file.isFile()){
				System.out.println("您输入的是文件名，请重新录入");
			}else {
				return file;
			}
		}
	}
	
	public static void print(File file, int level) {
		File[] arr = file.listFiles();
		for (File file2 : arr) {
			for (int i = 0; i <= level; i++) {
				System.out.print("\t");
			}
			if(file2.isFile()) {
				System.out.println(file2);	
			}else if(file.isDirectory()) {
				level++;
				System.out.println(file2);
				print(file2,level);
			}
		}	
	}
	
	public static void print2(File file, int level) {
		File[] arr = file.listFiles();
		for (File file2 : arr) {
			for (int i = 0; i < level; i++) {
				System.out.print("\t");
			}
			System.out.println(file2);	
			if(file2.isDirectory()) {
				print2(file2,level+1);
			}
		}	
	}
}
