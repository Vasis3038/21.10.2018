
# 21.10.2018
/*) Реализуйте структуру Rational для работы с рациональными числами, как с
несократимыми дробями. В программе должно присутствовать описание
структуры и программа показывающая работоспособность структуры.
Комментарий 1. Структура должна уметь работать с арифметикой и
сравнениями. С помощью структуры должна быть возможность создавать
пользовательские функции.
Комментарий 2. Программа должна содержать использование ВСЕХ
методов. На примере рациональных чисел посмотрите когда именно
вызываются методы. Для этого добавьте отладочную печать работающую
при их использовании. Например, “Copying Constructor is working”.
Комментарий 3. Последние 2 балла будут ставиться, если перегрузить
операторы ввода/вывода(без этого за задачу ставится не более 8 баллов).
Для выполнения этой части полезно
почитать:”http://www.amse.ru/courses/cpp2/2010_11_22.html”*/
#include <iostream>

using namespace std;

struct drob{
int ch;// ��������� / �������
int zn;// ����������� / -
};
struct Rational{
drob d1;//��������� � ����������� ������� �����
drob d2;//��������� � ����������� ������� �����
int reductionch(int n, int m){//���������� ���������
    if(n%2==0 and m%2==0)
{
    while(n%2==0 and m%2==0)
    {n = n/2;
     m = m/2;}
}
if(n%3==0 and m%3==0)
{
    while(n%3==0 and m%3==0)
    {n = n/3;
     m = m/3;}
}
if(n%5==0 and m%5==0)
{
    while(n%5==0 and m%5==0)
    {n = n/5;
     m = m/5;}
}
if(n%7==0 and m%7==0)
{
    while(n%7==0 and m%7==0)
    {n = n/7;
     m = m/7;}
}
    return (n);
}
int reductionz(int n, int m){//���������� �����������


    if(n%2==0 and m%2==0)
{
    while(n%2==0 and m%2==0)
    {n = n/2;
     m = m/2;}
}
if(n%3==0 and m%3==0)
{
    while(n%3==0 and m%3==0)
    {n = n/3;
     m = m/3;}
}
if(n%5==0 and m%5==0)
{
    while(n%5==0 and m%5==0)
    {n = n/5;
     m = m/5;}
}
if(n%7==0 and m%7==0)
{
    while(n%7==0 and m%7==0)
    {n = n/7;
     m = m/7;}
}
    return (m);
}
int multiplication(){//���������
    int n, m;//����� ��������� � ����� �����������
    n = d1.ch*d2.ch;
    m = d1.zn*d2.zn;
    Rational a;
    int h=n;
    n = a.reductionch(n,m);
     m = a.reductionz(h,m);
   cout << "numerator = " << n << "  denominator = " << m << endl;
}
int division(){//�������
    int n, m;//����� ��������� � ����� �����������
    n = d1.ch*d2.zn;
    m = d1.zn*d2.ch;
    Rational a;
    int h=n;
    n = a.reductionch(n,m);
     m = a.reductionz(h,m);

   cout << "numerator = " << n << "  denominator = " << m << endl;
}
int sum(){// ��������
    int n, m;//����� ��������� � ����� �����������
    n = d1.ch*d2.zn + d2.ch*d1.zn;
    m = d1.zn*d2.zn;
    Rational a;
    int h=n;
    n = a.reductionch(n,m);
     m = a.reductionz(h,m);
    cout << "numerator = " << n << "  denominator = " << m << endl;
}
int degree(){// ���������� � �������
    int n = d1.ch;
    int m = d1.zn;
    int s = d2.ch;
    if(s>0){
        for (int i = 1; i<s; i++)
        {
        n = n*n;
        m = m*m;
        }
         cout << "numerator = " << n << "  denominator = " << m << endl;
        }
    if(s<0){
        for (int i = 1; i<s; i++)
        {
        n = n*n;
        m = m*m;
        }
         cout << "numerator = " << m << "  denominator = " << n << endl;
    }
    if (s==0){
        n=1;
        m=1;
         cout << "numerator = " << n << "  denominator = " << m << endl;
    }

}
int difference(){// ���������
    int n, m;//����� ��������� � ����� �����������
    n = d1.ch*d2.zn - d2.ch*d1.zn;
    m = d1.zn*d2.zn;
    Rational a;
    int h=n;
    n = a.reductionch(n,m);
     m = a.reductionz(h,m);
        cout << "numerator = " << n << "  denominator = " << m << endl;
}
int more (){//���������� ��������
    int m, n, n1, n2;
    n1 = d1.ch*d2.zn;
    n2 = d2.ch*d1.zn;
    if (n1 > n2){
        n = d1.ch;
        m = d1.zn;
    }
        if (n2 > n1){
        n = d2.ch;
        m = d2.zn;
    }
        if (n1 = n2){
cout << "equal";
    }
    cout << "numerator = " << n << "  denominator = " << m << endl;
}
int less (){//���������� ��������
    int m, n, n1, n2;
    n1 = d1.ch*d2.zn;
    n2 = d2.ch*d1.zn;
    if (n1 < n2){
        n = d1.ch;
        m = d1.zn;
    }
        if (n2 < n1){
        n = d2.ch;
        m = d2.zn;
    }
        if (n1 = n2){
cout << "equal";
    }
    cout << "numerator = " << n << "  denominator = " << m << endl;
    }
};

int main(){
Rational a = {{6,4},{3,4}};//� �������� ������� ����������� ��������� � ����������� ������ � ������ ����� ����� �������
cout << a.multiplication() << endl;
    return 0;
}
