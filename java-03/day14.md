### File类

```java
练习一:相对路径和绝对路径的使用
描述:创建两个文件对象，分别使用相对路径和绝对路径创建。
答案
操作步骤:
绝对路径创建文件对象：使用File类一个参数的构造方法。
相对路径创建文件对象：使用File类两个参数的构造方法。
代码:
public class Test01_01 {
public static void main(String[] args) {
// 创建文件对象：绝对路径
		File f1 = new File("d:/aaa/a.txt");
		// 创建文件对象：相对路径
		File f2 = new File("a.txt");
	}
}
练习二:检查文件是否存在,文件的创建
描述:检查D盘下是否存在文件a.txt,如果不存在则创建该文件。
答案
操作步骤:
1.	使用绝对路径创建对象关联到D盘的a.txt。
2.	通过文件对象方法判断文件是否存在。
3.	不存在则调用创建文件的方法创建文件。
代码:
public class Test01_02 {
	public static void main(String[] args) throws IOException{
		// 创建文件对象：绝对路径
		File f = new File("d:/a.txt");
		// 如果文件不存在，则创建文件
		if(!f.exists()) {
			f.createNewFile();
		}
	}
}

练习三:单级文件夹的创建
描述:在D盘下创建一个名为bbb的文件夹。
答案
操作步骤:
1.	创建文件对象指定路径为d:/bbb
2.	调用文件对象创建文件夹的方法
代码:
public class Test01_03 {
	public static void main(String[] args) {
		// 创建文件对象
		File f = new File("d:/bbb");
		// 创建单级文件夹
		f.mkdir();
	}
}

练习四:多级文件夹的创建
描述:在D盘下创建一个名为ccc的文件夹，要求如下：
1.ccc文件夹中要求包含bbb子文件夹
2.bbb子文件夹要求包含aaa文件夹
答案:
操作步骤:
1.	创建文件对象关联路径：d:/ccc/bbb/aaa
2.	调用文件对象创建多级文件夹的方法
代码:
public class Test01_04 {
	public static void main(String[] args) {
		// 创建文件对象
		File f = new File("d:/ccc/bbb/aaa");
		// 创建多级文件夹
		f.mkdirs();
	}
}
练习五:删除文件和文件夹
描述:
将D盘下a.txt文件删除
将D盘下aaa文件夹删除,要求文件夹aaa是一个空文件夹。
答案:
操作步骤:
1.	创建文件对象关联路径：d:/a.txt
2.	调用文件对象删除文件的方法
3.	创建文件对象关联路径：d:/aaa
4.	调用文件对象删除文件夹的方法
代码:
public class Test01_05 {
	public static void main(String[] args) {
		// 创建文件对象
		File f = new File("d:/a.txt");
		// 删除文件
		f.delete();
		
		// 创建文件夹对象
		File dir = new File("d:/aaa");
		// 删除文件夹
		dir.delete();
	}
}
练习六:获取文件信息:文件名,文件大小,文件的绝对路径,文件的父路径
描述:
获取D盘aaa文件夹中b.txt文件的文件名，文件大小，文件的绝对路径和父路径等信息，并将信息输出在控制台。
答案:
操作步骤:
1.	在D盘aaa文件夹中创建一个b.txt文件并输入数据
2.	创建文件对象关联路径：d:/aaa/b.txt
3.	调用文件对象的相关方法获得信息并输出。可以通过API帮助文档查询方法。
代码:
public class Test01_06 {
	public static void main(String[] args) {
		// 创建文件对象
		File f = new File("d:/aaa/b.txt");
		// 获得文件名
		String filename = f.getName();
		// 获得文件大小
		longfilesize = f.length();
		// 获得文件的绝对路径
		String path = f.getAbsolutePath();
		// 获得父文件夹路径，返回字符串
		String parentPath = f.getParent();
		// 获得父文件夹路径，返回文件对象
		File parentFile = f.getParentFile();
		// 输出信息
		System.out.println("文件名：" + filename);
		System.out.println("文件大小：" + filesize);
		System.out.println("文件路径：" + path);
		System.out.println("文件父路径：" + parentPath);
		System.out.println("文件父路径：" + parentFile);
	}
}

练习七:文件夹或文件的判断
描述:
1.判断File对象是否是文件,是文件则输出：xxx是一个文件，否则输出：xxx不是一个文件。
2.判断File对象是否是文件夹,是文件夹则输出：xxx是一个文件夹，否则输出：xxx不是一个文件夹。(xxx是文件名或文件夹名)
答案:
操作步骤:
1.	创建两个文件对象分别关联到不同的文件，比如：d:/a.txt，d:/aaa
2.	调用文件对象的判断是否是文件或是否是文件夹的方法
3.	获得文件名，根据判断结果输出信息。
代码:
public class Test01_07 {
	public static void main(String[] args) {
		// 创建文件对象
		File f1 = new File("d:/b.txt");
		// 判断是否是一个文件
		if(f1.isFile()) {
			System.out.println(f1.getName()+"是一个文件");
		}  else {
			System.out.println(f1.getName()+"不是一个文件");
		}
		// 创建文件对象
		File f2 = new File("d:/aaaa");
		// 判断是否是一个文件夹
		if(f2.isDirectory()) {
			System.out.println(f2.getName()+"是一个文件夹");
		}  else {
			System.out.println(f2.getName()+"不是一个文件夹");
		}
	}
}

```

### IO字符流

```java
项目需求：请用户从控制台输入信息，程序将信息存储到文件Info.txt中。可以输入多条信息，每条信息存储一行。当用户输入：”886”时，程序结束。
答案
操作步骤:
1.	创建MainAPP类,并包含main()方法
2.	按照上述要求实现程序
代码:
public class Test01_07 {
	public static void main(String[]args) throws IOException {
		//1. 指定输出流， 对应的文件Info.txt
		FileWriter bw= new  FileWriter("Info.txt");
		//2.采用循环的方式，把每条信息存储一行到Info.txt中
		Scanner sc= new Scanner(System.in);
		while(true){
			//获取键盘输入的一行内容
			System.out.print("请输入内容：");
			String str= sc.nextLine();
			//当用户输入：”886”时，程序结束。
			if ("886".equals(str)) {
				break;//跳出循环
			}
			//把内容写入到Info.txt文件中
			bw.write(str);
			//换行
			bw.write(System.lineSeparator());
		}
		//关闭流
		bw.close();
	}
}

```

### IO字节流

```java
练习一:字节输出流写出字节数据
描述:利用字节输出流一次写一个字节的方式，向D盘的a.txt文件输出字符‘a’。
答案
操作步骤:
1.	创建字节输出流FileOutputStream对象并指定文件路径。
2.	调用字节输出流的write(int byte)方法写出数据
代码:
public class Test01_01 {
public static void main(String[] args) throws IOException {
		// 1.创建字节输出流FileOutputStream对象并指定文件路径。
		FileOutputStream fos = new FileOutputStream("d:/a.txt");
		// 2.调用字节输出流的write(int byte)方法写出数据
		fos.write(97);
		// 3.关闭流
		fos.close();
	}
}
练习二:字节输出流写出字节数组数据
描述:利用字节输出流一次写一个字节数组的方式向D盘的b.txt文件输出内容:"i love java"。
答案
操作步骤:
1.	创建字节输出流FileOutputStream对象并指定文件路径。
2.	调用字节输出流的write(byte[] buf)方法写出数据。
代码:
public class Test01_02 {
		public static void main(String[] args) throws IOException {
		// 1.创建字节输出流FileOutputStream对象并指定文件路径。
		FileOutputStream fos = new FileOutputStream("d:/b.txt");
		// 2.调用字节输出流的write(byte[] buf)方法写出数据。
		byte[] buf = "i love java".getBytes();
		fos.write(buf);
		// 3.关闭资源
		fos.close();
	}
}
练习三:文件的续写和换行输出
描述:在D盘下，有一c.txt 文件中内容为：HelloWorld 
在c.txt文件原内容基础上，添加五句 I love java，而且要实现一句一行操作(注：原文不可覆盖)。
利用字节输出流对象往C盘下c.txt文件输出5句：”i love java”

答案
操作步骤:
1.	利用两个参数的构造方法创建字节输出流对象，参数一指定文件路径，参数二指定为true
2.	调用字节输出流的write()方法写入数据，在每一行后面加上换行符:”\r\n”
代码:
public class Test01_03 {
	public static void main(String[] args) throws IOException{
		// 1.创建字节输出流FileOutputStream对象并指定文件路径,并追加方式
		FileOutputStream fos = new FileOutputStream("c:/c.txt",true);
		// 2.调用字节输出流的write方法写出数据
		// 2.1 要输出的字符串
		String content = "i love java \r\n";
		for (int i = 0; i< 5; i++) {
			fos.write(content.getBytes());
		}
		// 3.关闭流
		fos.close();
	}
}
练习四:字节输入流一次读取一个字节数据
描述:利用字节输入流读取D盘文件a.txt的内容，文件内容确定都为纯ASCII字符
,使用循环读取，一次读取一个字节，直到读取到文件末尾。将读取的字节输出到控制台
答案
操作步骤:
1.	创建字节输入流对象指定文件路径。
2.	调用read(byte b)方法循环读取文件中的数据
3.	直到读取到-1时结束读取
代码:
public class Test01_04 {
	public static void main(String[] args) throws IOException{
		// 创建字节输入流对象并关联文件
		FileInputStream fis = new FileInputStream("d:/a.txt");
		// 定义变量接收读取的字节
		int len = -1;
		// 循环从流中读取数据
		while((len = fis.read()) != -1) {
			System.out.print((char)len);
		}
		// 关闭流
		fis.close();
	}
}
练习五:字节输入流一次读取一个字节数组数据
描述:利用字节输入流读取D盘文件b.txt的内容，文件内容确定都为纯ASCII字符
,使用循环读取，一次读取一个字节数组，直到读取到文件末尾，将读取到的字节数组转换成字符串输出到控制台。
答案
操作步骤:
1.	创建字节输入流对象指定文件路径。
2.	定义一个字节数数组，用来存放读取的字节数
3.	调用read(byte[] buf)方法传入字节数组，循环读取文件中的数据
4.	直到读取到-1时结束读取
代码:
public class Test01_05 {
	public static void main(String[] args) throws IOException{
		// 创建字节输入流对象并关联文件
		FileInputStream fis = new FileInputStream("d:/b.txt");
		// 定义字节数组存放读取的字节数
		byte[] buffer = new byte[1024];
		// 定义变量接收读取的字节
		int len = -1;
		// 循环从流中读取数据
		while((len = fis.read(buffer)) != -1) {
			System.out.print(new String(buffer,0,len));
		}
		// 关闭流
		fis.close();
	}
}
练习六:字节流复制文件
描述:利用字节流将E盘下的a.png图片复制到D盘下(文件名保存一致)
要求：
一次读写一个字节的方式
答案
操作步骤:
1.	创建字节输入流对象关联文件路径：E盘下的a.png
2.	创建字节输出流对象关联文件路径：D盘下的a.png
3.	使用循环不断从字节输入流读取一个字节，每读取一个字节就利用输出流写出一个字节。
4.	关闭流，释放资源
代码:
public class Test01_06 {
	public static void main(String[] args) throws IOException {
		// 创建字节输入流对象并关联文件
		FileInputStream fis = new FileInputStream("e:/a.png");
		// 创建字节输出流对象并关联文件
		FileOutputStream fos = new FileOutputStream("d:/a.png");
		// 定义变量接收读取的字节数
		int len = -1;
		// 循环读取图片数据
		while((len = fis.read()) != -1) {
			// 每读取一个字节的数据就写出到目标文件中
			fos.write(len);
		}
		// 关闭流
		fis.close();
		fos.close();
	}
}

```

