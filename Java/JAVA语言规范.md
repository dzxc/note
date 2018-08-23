# Java语言规范
### 语法定义

      IfThenStatement:
          if ( Expression ) Statement  // if(true){do sth;}
      
      ArgumentList:  //add(a,b,c,d);
      	Argument
      	ArgumentList , Argument


### 词法结构
    Identifier:
        IdentifierChars but not a Keyword or BooleanLiteral or NullLiteral
    
    IdentifierChars:
        JavaLetter
        IdentifierChars JavaLetterOrDigit
    
    JavaLetter:
        any Unicode character that is a Java letter (see below)
    
    JavaLetterOrDigit:
        any Unicode character that is a Java letter-or-digit (see below)

\u + 4个16进制数字 表示UTF-16
行终结符： CR, or LF, or CR LF.
空白符
空格 tab \t 换页 \f  行终结符
注释
标示符
关键字


public static void 打印(){
System.out.println("中文方法哦");
}
public  static void main(String[] args) {
打印();
}


词法结构

    Int
    0 2 0372 0xDada_Cafe 1996 0x00_FF__00_FF
    Long
     0l 0777L 0x100000000L 2_147_483_648L 0xC0B0L
    Float
    1e1f 2.f .3f 0f 3.14f 6.022137e+23f
    Double
    1e1 2. .3 0.0 3.14 1e-9d 1e137
    操作
    +=  -=  *=  /=  &=  |=  ^=  %=  <<=  >>=  >>>=
    


### 类型和变量
#### 元类型 
byte short int long float char

变量初始值
int -> 0
boolean -> false
char ->\u0000

泛型

