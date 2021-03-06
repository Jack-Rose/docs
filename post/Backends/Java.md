# Java

## 封装

### Java中的内部类

#### 作用

1. 内部类提供更好的封装，不允许同一个包中其他类访问该类
2. 内部类可直接访问外部类的所有数据（包括私有数据）

#### 分类

1. 成员内部类
2. 静态内部类
3. 方法内部类
4. 匿名内部类

```java
    public class HelloWorld {//外部类

        public class Inner {//内部类
            public void show(){
                System.out.println("我是内部类的方法");
            }
        }

        public static void main(String[] args){

            HelloWorld hello = new HelloWorld();//创建外部类对象

            Inner i  = hello.new Inner();//创建内部类的对象

            i.show();//调用内部类的方法
        }
    }
```

##### 成员内部类

###### 注意点

1. 创建一个内部类对象：   内部类 对象名 = 外部类对象.new 内部类().
2. 外部类不能直接使用内部类点成员和方法,需现创建内部类对象.
3. 如果外部类和内部类具有相同的成员变量或方法，内部类默认访问自己的成员变量或方法，如果要访问外部类的成员变量，可以使用 this 关键字

```java
public class HelloWorld{
    //外部类的私有属性name
    private String name = "github";
    //外部类的成员属性
    int age = 20;
    //成员内部类Inner
    public class Inner {
        String name = "github";
        //内部类中的方法
        public void show() {
            System.out.println("外部类中的name：" +HelloWorld.this.name);
            System.out.println("内部类中的name：" +name);
            System.out.println("外部类中的age：" + age);
        }
    }

    //测试成员内部类
    public static void main(String[] args) {
        //创建外部类的对象
        HelloWorld o = new HelloWorld ();
        //创建内部类的对象
        Inner inn =  o.new Inner();
        //调用内部类对象的show方法
        inn.show();
    }
}
```

##### 静态内部类

> 静态内部类是 static 修饰的内部类

1. 创建静态内部类的对象时，不需要外部类的对象，可以直接创建 内部类 对象名= new 内部类();
2. 静态内部类不能直接访问外部类的非静态成员，但可以通过 new 外部类().成员 的方式访问;
3. 如果外部类的静态成员与内部类的成员名称相同，可通过“类名.静态成员”访问外部类的静态成员;
4. 如果外部类的静态成员与内部类的成员名称不相同，则可通过“成员名”直接调用外部类的静态成员;

## 常用内部类

### 包装类

> 基本类型数据类型有对应点包装类

除了下面两个类型不是转化 首字母大写。其他都是

| 基本类型 | 对应包装类 |
| -------- | :--------: |
| int      | Integer    |
| char     | Character  |

#### 基本类型和包装类型之间的转换

##### 装箱

```java

    // 定义double类型变量
double a = 91.5;

    // 手动装箱
Double b = new Integer(a)

    // 自动装箱
Double c = a

```

##### 拆箱

```java
Double d = new Double(87.0);

// 手动拆箱
double e = d.doubleValue();

// 自动拆箱
double f = d;

```

#### 基本数据类型和字符串之间的转化

>常用的三种方法

1. 包装类的toString方法
2. String类的valueOf()方法
3. 用一个空字符串加上基本数据类型

```java
double m = 88.5;
//将基本类型转换为字符串
String str1 = String.valueOf(m);

String str = "150.20";
// 将字符串转换为基本类型
Double a = Double.parseDouble(str);
```

#### Date && Calendar

```java
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;

public class HelloWorld {
    public static void main(String[] args) {
            // 创建Calendar对象
            Calendar c = Calendar.getInstance();

            // 将Calendar对象转换为Date对象
            Date date = c.getTime();

            // 创建SimpleDateFormat对象，指定目标格式
            SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");

            // 将日期转换为指定格式的字符串
            String now = sdf.format(date);
            System.out.println("当前时间：" + now);
        }
    }
```