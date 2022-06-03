#include<stdio.h>
#include <string.h>

struct Account//定义账户
{   
 char name[100];
 char idCard[19];
 char username[100];
 char password[7];
 char tel[12];
 char balance[100];
 float money;
};

typedef struct Account Account;

Account a[100];
int i = 0;


void signIn()//登录
{
 FILE* fp = fopen("D:/atm.txt", "r");
 if (fp != NULL)
 {
  int j = 0;
  while (!feof(fp))
  {
   fscanf(fp,"%s\t%s\t%s\t%s\t%s\n",
    a[j].name, a[j].idCard, a[j].username, a[j].password, a[j].tel);
   j++;
  }
 }
}


void signUp1()//开户（中文）
{
 printf("请输入姓名：\n");
 scanf_s("%s", a[i].name, sizeof(a[i].name));

 printf("请输入身份证：\n");
 scanf_s("%s", a[i].idCard, sizeof(a[i].idCard));

 printf("请输入账号：\n");
 scanf_s("%s", a[i].username, sizeof(a[i].username));

 printf("请输入密码：\n");
 scanf_s("%s", a[i].password, sizeof(a[i].password));

 printf("请输入电话：\n");
 scanf_s("%s", a[i].tel, sizeof(a[i].tel));

 a[i].money = 0.0f;
 

 FILE* fp = fopen("D:/atm.txt", "a");//存入文件（a表示追加写入）
 if (fp != NULL)
 {
  fprintf(fp, "%s\t%s\t%s\t%s\t%s\n",
   a[i].name, a[i].idCard, a[i].username, a[i].password, a[i].tel);
  fclose(fp);
 }

 i++;
 printf("注册成功!\n");
 printf("请继续按菜单操作\n");
}

void signUp2()//开户（英文）
{
 printf("Please enter your name：\n");
 scanf_s("%s", a[i].name, sizeof(a[i].name));

 printf("Please enter your ID number：\n");
 scanf_s("%s", a[i].idCard, sizeof(a[i].idCard));

 printf("Please enter the account number：\n");
 scanf_s("%s", a[i].username, sizeof(a[i].username));

 printf("Please input a password：\n");
 scanf_s("%s", a[i].password, sizeof(a[i].password));

 printf("Please enter your mobile number：\n");
 scanf_s("%s", a[i].tel, sizeof(a[i].tel));

 a[i].money = 0.0f;


 FILE* fp = fopen("D:/atm.txt", "a");//存入文件（a表示追加写入）
 if (fp != NULL)
 {
  fprintf(fp, "%s\t%s\t%s\t%s\t%s\n",
   a[i].name, a[i].idCard, a[i].username, a[i].password, a[i].tel);
  fclose(fp);
 }
 i++;

 printf("Created successfully!\n");
 printf("Please continue to press the menu\n");
}

void printAllAccount()//打印所有账户
{
 for (int j = 0; j < i; j++)
 {
  printf("%s\t%s\n", a[j].name, a[j].username);
 }
}

void showChineseMenu()//中文菜单
{
 printf("按1,登录\n");
 printf("按2,开户\n");
 printf("按3,退出\n");
 printf("按4,打印所有帐户\n");
 while (1)
 {
  char c;
  scanf_s(" %c", &c, sizeof(c));
  if (c == '1')
  {
   signIn();
  }
  else if (c == '2')
  {
   signUp1();
  }
  else if (c == '3')
  {
   return;
  }
  else if (c == '4')
  {
   printAllAccount();
  }
 }
}

void showEnglishMenu()//英文菜单
{
 printf("A,log on\n");//登录
 printf("B,establish an account\n");//开户
 printf("C,logout\n");//退出

 while (1)
 {
  char c;
  scanf_s(" %c", &c, sizeof(c));
  if (c == 'A')
  {
   signIn();
  }
  else if (c == 'B')
  {
   signUp2();
  }
  else if (c == 'C')
  {
   return;
  }
 }
}

int main()
{
 printf("按1,显示中文\n");
 printf("Input 2,Show English\n");
 char c;
 scanf_s("%c", &c, sizeof(c));
 if (c == '1')
 {
  //显示中文菜单 
  showChineseMenu();
 }
 else if (c == '2')
 {
  //显示英文菜单 
  showEnglishMenu();
 }
 return 0;
}
