#include<iostream>
#include<cstdio>
#include<cstdlib>
using namespace std;
#define SIZE 50
char s[SIZE];
int top=-1;
void push(char elem)
{

    s[++top]=elem;include
}
char pop()
{
 return(s[top--]);
}
int pr(char elem)
{
    switch(elem)
    {
        case '#':return 0;
        case '(':return 1;
        case '+':
            case '-':return 2;
            case '*':
                case '/':return 3;
    }
}
int main()
{
    char infx[50],postfx[50],ch,elem;
    int i=0,k=0;
    cout<<"\nEnter the infix Expression:";
    cin>>infx;
    push('#');
    while((ch=infx[i++])!='\0')
    {
        if(ch=='(')
            push(ch);
        else
            if(isalnum(ch))
            postfx[k++]=ch;
        else
            if(ch==')')
        {
            while(s[top]!='(')
                    postfx[k++]=pop();
            elem=pop();
        }
        else{
            while(pr(s[top])>=pr(ch))
                postfx[k++]=pop();
            push(ch);
        }
    }
    while(s[top]!='#')
        postfx[k++]=pop();
    postfx[k]='\0';
    cout<<"\nPostfix Expression:\n"<<postfx;
    return 0;
}
