//MATLAB多项式运算与符号运算

利用多项式运算和符号表达式运算十分方便，下面总结了一些常用的函数，并附上自己编写的将s域变换到z域的函数

多项式运算

1.r=roots(p)多项式求根

2.p3=conv(p1,p2)多项式相乘

3.p1=polyder(p)多项式求导

3.polyval(p,x)多项式代入求值

4.polyfit(x,y,n)多项式拟合

5. [r,p,k] =residue(b,a)部分分式展开

注：多项式运算的函数都是以向量来表示的，注意与符号表达式的区别，两者间可以相互转换 poly2sym(),sym2poly()

 

符号运算

1.syms x,y,z; 定义符号变量

2.sym=poly2sym(p,’s’);将多项式向量转换成符号表达式
%poly2sym的有关用法可以查看其他文档

3.p=sym2poly(sym);将符号表达式转化成多项式向量

4.[N,D]=numden(sym);将符号表达式分离出分子分母

5.subs(sym,’x’,value)符号表达式代数求值

6. simplify(sym)化简

7.pretty(sym)美化输出符号表达式

8.expand(sym)展开

9.collect(sym)合并

10.solve(sym)求解sym=0的解。



function [numz,denz]=s2z(nums,dens,Ts)
%[numz,denz]=s2z(nums,dens,Ts)
%功能：将s域传递函数变换到z域
%输入：
%nums,dens 连续系统以s为变量分子，分母多项式
%输出：
%numz，denz 离散系统以z为变量分子，分母多项式
syms t n s z;
Gs_num=poly2sym(nums);
Gs_den=poly2sym(dens);
Gs=Gs_num/Gs_den;
ft=ilaplace(Gs); %对连续传函Laplace反变换
Gnt=subs(ft,t,n*Ts); %离散化
Gz=ztrans(Gnt); %z变换
[a,b]=numden(Gz); %numden函数将符号表达式的分子与分母分离
numz=sym2poly(a);
denz=sym2poly(b);
end
