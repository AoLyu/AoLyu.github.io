## Qt信号函数重载时connect写法

无参和有参两个函数

### Qt5版本-函数指针

```c++
//函数指针区别信号重载 ---右边注释是书写时的注意事项
//出现信号重载 Qt5的connect写法：
void (MyWidget::*myS1)()=&MyWidget::mySignal;               //注意等号后面只需加函数名 不要加括号
void (MyWidget::*myS2)(int,QString)=&MyWidget::mySignal;    //与普通函数指针区别是在等号前加“MyWidget::”后面加作用域“&MyWidget::”
connect(this,myS1,this,&MyWidget::dealMySignal1);           //处理无参 //myS1的位置不需要再加作用域
connect(this,myS2,this,&MyWidget::dealMySignal2);           //处理有参
```

### Qt4版本-SIGNAL和SLOT

```c++
/*当出现重载信号 Qt4的connect写法（上面是Qt5写法）：
1）槽函数必须带有solts关键字 且要带有访问权限(公有保护私有)
2)使用SIGNAL和SLOT两个宏来书写信号和槽
2）编译时他不会进行错误检查   只是将函数名字当成字符串
*/
connect(this,SIGNAL(mySignal()),this,SLOT(dealMySignal1()));
connect(this,SIGNAL(mySignal(int,QString)),this,SLOT(dealMySignal2(int,QString)));
```

