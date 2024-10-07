# dsa3456



Program 03

#include<stdio.h>
#define MAX 3
int s[MAX],top=-1,ele,i;
void push(int ele)
{
if(top==MAX-1)
 {
 printf("Stack Over flow");
 return;
 }
top++;
s[top]=ele;
}
int pop()
 {
int ele;
if(top==-1)
 {
 printf("Stack underflow");
 return;
}
ele=s[top];
top--;
return ele;
 }
void display()
{
if(top==-1)
 {
printf("Stack underflow");
 return;
}
printf("Stack Contents are\n");
for(i=top;i>=0;i--)
printf("%d\n",s[i]);
}
void pal()
{
top=-1;
int i=1,len=0,rev=0,digit,temp,n;
printf("Enter a Number\n");
scanf("%d",&n);
temp=n;
while(n!=0)
{
digit=n%10;
n=n/10;
push(digit);
len++;
}
while(len!=0)
{
digit=pop();
rev=rev+(digit*i);
len--;
i=i*10;
}
if(temp==rev)
printf("Number is a palindrome");
else
printf("Number is not a palindrome");
}
void main()
{
int ch;
do
{
printf(“1:push 2:pop 3:display 4:palindrome\n”);
printf("Enter your choice\n");
scanf("%d",&ch);
switch(ch)
{
case 1: 
printf("Enter the element to be pushed \n");
scanf("%d",&ele);
push(ele);
break;
case 2:
ele=pop();
printf("Element deleted is %d",ele);
break;
case 3:
display();
break;
case 4:
pal();
break;
default: printf("invalid choice\n");
}
}while(ch<=4);
}










Program 04




#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

#define MAX 25

char infix[MAX], postfix[MAX];
char stack[MAX];
int top = -1;

void push(char c) {
    if (top >= MAX - 1) {
        printf("Stack Overflow\n");
        exit(1);
    }
    stack[++top] = c;
}

char pop() {
    if (top == -1) {
        printf("Stack Underflow\n");
        exit(1);
    }
    return stack[top--];
}

int precedence(char c) {
    switch (c) {
        case '+':
        case '-': return 1;
        case '*':
        case '/': return 2;
        case '^': return 3;
        case '(': return 0;
    }
    return -1;
}

int main() {
    int i, j = 0;
    char ch;

    printf("Enter the infix expression:\n");
    scanf("%s", infix);

    push('#');

    for (i = 0; infix[i] != '\0'; i++) {
        ch = infix[i];
        
        if (isalnum(ch)) {
            postfix[j++] = ch;
        } else if (ch == '(') {
            push(ch);
        } else if (ch == ')') {
            while (stack[top] != '(') {
                postfix[j++] = pop();
            }
            pop();
        } else {
            while (precedence(stack[top]) >= precedence(ch)) {
                postfix[j++] = pop();
            }
            push(ch);
        }
    }

    while (stack[top] != '#') {
        postfix[j++] = pop();
    }
    postfix[j] = '\0';

    printf("Postfix expression is: %s\n", postfix);
    
    printf("Press Enter to exit...");
    getchar();
    getchar();

    return 0;
}













Program 05



first   




#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<math.h>
int op1,op2,res,i,top=-1,s[10],ele,n;
void push(int ele)
 {
 top++;
 s[top]=ele;
 }
 int pop()
 {
 int ele;
 ele=s[top];
 top--;
 return(ele);
 }
void main()
{
int e;
char postfix[20],ch;
printf("enter the postfix exp\n");
scanf("%s",postfix);
for(i=0;postfix[i]!='\0';i++)
{
ch=postfix[i];
if(isdigit(ch))
push(ch-'0');
else
{
op2=pop();
op1=pop();
switch(ch)
{
case '+':res=op1+op2;
 break;
case '-':res=op1-op2;
 break;
case '*':res=op1*op2;
 break;
case '/':res=op1/op2;
 break;
case '^':res=pow(op1,op2);
 break;
}
push(res);
}
}
 printf("result of postfix exp %d",res);
}






second (tower of hanoi)



#include <stdio.h>

void tow(int n, char s, char t, char d) {
    if (n == 1) {
        printf("Move disk 1 from %c to %c\n", s, d);
        return;
    }
    tow(n - 1, s, d, t);
    printf("Move disk %d from %c to %c\n", n, s, d);
    tow(n - 1, t, s, d);
}

int main() {
    int n;
    printf("Enter the number of disks:\n");
    scanf("%d", &n);
    tow(n, 's', 't', 'd');
    return 0;
}













Program 06




#include<stdio.h>
#define MAX 3
int cq[MAX],f=0,r=-1,i,j,c=0,n,ele;
void insert()
{
if(c==MAX)
{
printf("CIRCULAR QUEUE OVERFLOW|n");
return;
}
printf("enter the value\n");
scanf("%d",&ele);
r=(r+1)%MAX;
cq[r]=ele;
c++;
}
void delete_ele()
{
if(c==0)
{
printf("CIRCULAR QUEUE UNDERFLOW|n");
f=0,r=-1;
return;
}
printf("element deleted is %d",cq[f]);
f=(f+1)%MAX;
c--;
}
void display()
{
j=f;
if(c==0)
{
printf("CIRCULAR QUEUE UNDERFLOW|n");
return;
}
printf("contents of CQ are\n");
for(i=1;i<=c;i++)
{
printf("%d\t", cq[j]);
j=(j+1)%MAX;
}
}
void main()
{
int ch;
do
{
printf("1:insert 2:delete 3:display \n");
printf("enter your choice\n”);
scanf("%d",&ch);
switch(ch)
{
case 1:insert();
break;
case 2:delete_ele();
break;
case 3:display();
break;
default:printf("invalid choice\n");
}
}while(ch<=3);
}
