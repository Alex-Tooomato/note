# 函数指针的缺点

无法只有自己的状态，也就是局部状态。返回的指针不能是局部变量，否则返回后就在栈内自动释放。第二个缺点是适配性差

```c++
int a = 0;//静态全局变量区
char *p1; //编译器默认初始化为NULL
void main()
{
int b; //栈
char s[] = “abc”;//栈
char *p2 = “123456”;//123456在字符串常量区，p2在栈上
static int c =0; //c在静态变量区，0为文字常量，在代码区
const int d=0; //栈
static const int d;//静态常量区
p1 = (char *)malloc(10);//分配得来得10字节在堆区。
strcpy(p1, “123456”); //123456放在字符串常量区，编译器可能会将它与p2所指向的"123456"优化成一个地方
}
```

