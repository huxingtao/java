## 标识符

### Java标识符命名规则：
1. 由字母、数字、下划线（_）和美元符号（\$ 音：dollar）组成。
2. 不能以数字开头。
3. 区分大小写。
4. 不能是Java中的保留字和关键字。

###变量：保存程序执行过程中的数据
- 变量名：定义变量的标识符
- 变量类型：存放的数据类型
- 变量值：内存单元中装载的数据
### 命名规范
- 变量名、方法名：首字母小写，其余单词首字母大写
- 类名、项目名：首字母大写，其余单词首字母大写
- 包名：全部小写，用英文的.隔开
- 常量：全部大写，单词之间用_隔开

- 总体原则：驼峰式，见名知义，便于代码的统一及可读性

### 基本数据类型
Java中定义了4类/8种基本数据类型

1. 布尔型---- boolean
2. 字符型---- char
3. 整数型---- byte, short, int, long
4. 浮点数型---- float, double

#### 整数类型
|类型  |占用存储空间|存储范围|
|---- | ------   | ------|
|byte |1字节    	 |-128 ~ 127 |
|short|2字节		 |	-2<sup>15</sup> ~ 2<sup>15</sup>-1|
|int  |4字节		 |-2<sup>31</sup> ~ 2<sup>31</sup>-1 |
|long |8字节		 |-2<sup>63</sup> ~ 2<sup>63</sup>-1 |

> Java语言整型数值默认为int，如：`int i = 3;`  
> 声明long类型可以加‘l’或‘ L’，如：`long  l = 3L;`  
> 赋值时不能超出该类型的数值范围

#### 浮点类型
|类    型|	占用存储空间|	存储范围
|---- | --------  | ------|
|float|	4字节 	|-3.403E38~3.403E38|
|double|8字节	| -1.798E308 ~1.798E308|

- 一般整数用int，小数用double 
- float： 小数位数少，单精度
- Java浮点型默认为double型，如要声明float型，则需在数字后面加f或F，如：
  `double  d = 3.14`  `float  f = 3.14f`

#### 字符类型
- char型数据用来表示通常意义上“字符” (单引号)
 - `char c = 'A';`  `char gender = '女"'; 
- Java字符采用Unicode编码，每个字符占两个字节，因而可用十六进制编码形式表示(Unicode是全球语言统一编码)
 - `char  c1 = '\u0061';	//相当于a`
 - `char c2=97;		//ASCII码，相当于a`
- Java语言中还可以使用转义字符'\'来将其后的字符转变为其它含义：
 - `char c2 = '\t';`

#### 引用类型

- String型数据用来表示通常意义上“字符串” （双引号）
 - `String h = "abc";`

#### 布尔类型
- boolean类型表示真假，一般用于逻辑运算、流程控制 
- boolean类型数据值：true或false，不可以用0、非0数字，大写代替。
- 示例：
 - `boolean  b = false;`
 - `boolean c = true;`

##### 转义字符
|  | 名称	|描述|
|---- | --------  | ------|
|\n 	|换行	|将光标移到下一行的第一格。
|\t 	|水平制表 	|将光标移到下一个水平制表位置。
|\'  	|单引号	|产生一个单引号。
|\"  	|双引号	|产生一个双引号。
|\\		|斜杠	|产生一个斜杠。

### 基本数据类型—类型转换

- 自动类型转换：取值范围小的自动转为取值范围大的
 - byte, short, int → long → float → double
 - char → int → long → float → double
 - short,char不会互相转换
 - 整个表达式的值不足int时，自动提升为int

- 强制类型转换：取值范围大的强制转为取值范围小的 如：
 - `long l = 100L;` `int i = (int)l;`
 - 注意：有可能造成精度降低或数据溢出，使用时要注意

- boolean 类型不能转换成任何其它基本数据类型

## 运算符

1. 算术运算符：+ 、 - 、 * 、 / 、 % 、 ++ 、 --
2. 字符串连接运算符：+
3. 赋值运算符：= 、 += 、 -= 、 *= 、 /= 、 %=
4. 关系运算符：> 、 < 、 >= 、 <= 、 == 、 !=
5. 逻辑运算符：&& 、 ||、!、 & 、 | 、 ^
6. 三目运算符：? : 
7. 位运算符：& 、 | 、 ^ 、 ~ 、 >> 、 << 

例子

- i++与++i的区别  
 - `int n = i++; // n = i = 2 i = i++ = 3`  
 - `int m = ++i; // i = i++ = 4 m = i = 4`
- 任意类型的值与String字符串类型拼接后全部转换成String字符串


### 位运算

|符号	|名称	|英文	|操作|
|---- | --------  | ------|-----|
|&	|按位与	|AND	|两个运算数为1，则结果为1|
|&#124;	|按位或	|OR	|两个运算数有一个为1，则结果为1|
|^	|按位异或	|XOR	|两个运算数不同时，则结果为1|
|~	|按位非	|NOT	|对每一个运算数按位取反|
|>>	|右移	|	|右移动，左边补0|
|<<	|左移	|	|左移动，右边补0|

- && 且 前面满足以后后面不会进行
- || 或 前面满足以后后面不会进行

### 三目运算

- 语法：逻辑判断（表达式是否成立） ? 结果1 ： 结果2
- 说明：表达式为boolean类型，先计算它的值，若为true，整个三目运算的结果为值1，否则为值2
- 例：
 - `int score = 75;`
 - `String type = score >=60 ? "及格" : "不及格";`
 - `System.out.println(3>4?1:2); // true返回结果1 false返回结果2`

### 常量
- 常量的值不能被修改   
- 常量名必须大写   
```
final double PI = 3.14；
final char MALE=‘M’，FEMALE=‘F’；
```
- 常量也可以首先声明，然后再进行赋值，但是只能赋值一次
```
final int UP；
UP = 1；
```

## 流程控制

### if else语句

```java
int a = sc.nextInt();  
if (a>=0 && a<60) {
    System.out.println("不及格");
} else if(a>=60 && a<80) {
    System.out.println("合格");
} else if (a>=80 && a<=100) {
        System.out.println("优秀");
} else {
    System.out.println("输入有误");
} 
```
- if else 结构初始值可以不用定义，因为if else 一定会进入一个

### 嵌套if语句
string类型字符串比较是否相等，需要用java自带的equals方法判断

```java
System.out.println("请输入用户名：");
String username = sc.nextLine();
System.out.println("请输入密码：");
String password =  sc.nextLine();
// string类型字符串比较是否相等，需要用java自带的equals方法判断
//.引出当前对象的所有已存在的方法或值
//第一个string类型的变量.equals(比对String类型的变量)
if (username.equals("admin")) {
    if (password.equals("123")) {
        System.out.println("登陆成功");
    } else {
        System.out.println("登录失败，密码错误");
    }
} else {
    System.out.println("登录失败，用户名错误");
}
```

### switch分支

```java
switch(表达式expr) {
    case const1:
        statement1;
        break;
    case const2:
        statement2;
        break;
    … …
    case constN:
        statementN;
        break;

    [default:
        statement_dafault;
        break;]
} 
```
- 表达式expr的值必须是以下几种类型之一：
 - char，byte，short，int，enum；
 - java7之后可以是String
 - 不能用boolean，long，float，double等其他类型
- case子句中的值const 必须是常量值，是一个点值，不能是一个范围
- 所有case子句中的值不能重复，否则编译出错
- default子句是可选的
- break语句用于执行完一个case分支后跳出switch语句块；如果没有，造成case贯穿

