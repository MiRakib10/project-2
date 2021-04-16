#include<string.h>
#include<stdio.h>
#include <time.h>
#include <stdlib.h>
#include<windows.h>
#include <conio.h>
#include<ctype.h>
#include <process.h>
int start();
int menu();
int reg();
int Food();
int payment();
int adstrt();
int adlogin();
int adreg();
int admenu();
int ckfood();
int main()
{
    printf("\t\t\tWELCOME TO\n\t\tONLINE FOOD ORDER SERVICE\n");
    printf("\t\t------------------------------");
    printf("\n\n\n");
    printf("Prepared by:\n");
    printf("-----------\n\n\n");
    printf("\t\t\t TEAM TR \n\t\t\tID:-173-35-2259\n");
    printf("\t\tDepartment of ECE\n");
    printf("\t\t North South University \n\n\n\n");
    printf("press any key to continue.....");
    getch();
     system("CLS");
    logo();
    int a;
    printf("\n\n\n\n");
    printf("\nPress '1' for Customer\n\n");
    printf("Press '2' for Manager\n\n\n");
    printf("Enter your choice:- ");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        start();
        break;
    case 2:
        system("CLS");
        adstrt();
        break;
    }
}
void gotoxy(int x, int y)
{
    COORD c;
    c.X=x;
    c.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),c);
}
adstrt()
{
    char ui[10],pw[10];
    int n;
    system("CLS");
    logo();

     printf("\n\n\n\n");
    printf("\nPress '1' for registration\n\nPress '2' for login\n\n\n");
    printf("Enter your choice:- ");
    scanf("%d",&n);
    switch(n)
    {
    case 1:
        system("CLS");
        logo();
        printf("\n\n\n\n");
        printf("\t\t\tREGISTRATION\n\t\t\t--------------\n\n\n");
        adreg();
        break;
    case 2:
        system("CLS");
        adlogin();
        break;
    }
    system("CLS");
}
struct adlogin
{
    char fname[100],lname[100],username[100],password[100];
};
struct login
{
    char fname[100],lname[100],username[100],password[100];
};
adreg()
{
    char fname[100],lname[100],username[100],password[100];
    FILE*log;
    log=fopen("login.txt","a");
    struct adlogin l;
    fflush(stdin);
    printf("Enter first name:- ");
    scanf("%s",&l.fname);
    printf("Enter last name:- ");
    scanf("%s",&l.lname);
    printf("Enter User name:- ");
    scanf("%s",&l.username);
    printf("Enter password:- ");
    scanf("%s",&l.password);
    fwrite(&l,sizeof(l),1,log);
    fclose(log);
    fflush(stdin);
    Sleep(100);
    printf("\n\nYour user name is your userID\n");
    Sleep(100);
    printf("Now login with your user id and password\n");
    Sleep(100);
    printf("\nPress any key to continue......");
    getch();
    system("CLS");
    adlogin();
}
adlogin()
{
    logo();
    printf("\n\n\n\n");
    printf("\t\t\tLOG IN\n\t\t\t--------\n");
    printf("Please enter your user id and password\n");
    char username[200],password[20];
    FILE*log;
    log=fopen("login.txt","r");
    struct adlogin l;
    fflush(stdin);
    printf("\nUSER ID:-");
    scanf("%s",&username);
    printf("Password:-");
    scanf("%s",&password);
    system("CLS");
    printf("LOADING\n");
    int i;
    for(i=0;i<=20;i++)
    {
        Sleep(20);
        printf("*");
    }
    while(fread(&l,sizeof(l),1,log))
    {
        if(strcmp(username,l.username)==0 && strcmp(password,l.password)==0)
        {
            system("CLS");
            Sleep(100);
            printf("Successful login....\n");
            Sleep(100);
            printf("Press any key to continue...");
            getch();
            system("CLS");
            admenu();
            fclose(log);
        }



    }

            printf("\nPlease enter correct user id or password...!\n");
            getch();
    fclose(log);
    fflush(stdin);
    system("CLS");

}
reg()
{
    char fname[100],lname[100],username[100],password[100];
    FILE*log;
    log=fopen("loginn.txt","a");
    struct login l;
    printf("Enter first name:- ");
    scanf("%s",&l.fname);
    printf("Enter last name:- ");
    scanf("%s",&l.lname);
    printf("Enter User name:- ");
    scanf("%s",&l.username);
    printf("Enter password:- ");
    scanf("%s",&l.password);
    fwrite(&l,sizeof(l),1,log);
    fclose(log);
    Sleep(100);
    printf("\n\nYour user name is your userID\n");
    Sleep(100);
    printf("Now login with your user id and password\n");
    Sleep(100);
    printf("\nPress any key to continue......");
    getch();
    system("CLS");
    login();
}
login()
{
    logo();
    printf("\n\n\n\n");
    printf("\t\t\tLOG IN\n\t\t\t--------\n");
    printf("Please enter your user id and password\n");
    char username[200],password[20];
    FILE*log;
    log=fopen("loginn.txt","r");
    struct login l;
    printf("\nUSER ID:-");
    scanf("%s",&username);
    printf("Password:-");
    scanf("%s",&password);
    system("CLS");
    printf("LOADING\n");
    int i;
    for(i=0;i<=20;i++)
    {
        Sleep(15);
        printf("*");
    }
    while(fread(&l,sizeof(l),1,log))
    {
        if(strcmp(username,l.username)==0 && strcmp(password,l.password)==0)
        {
            system("CLS");
            Sleep(100);
            printf("Successful login....\n");
            Sleep(100);
            printf("Press any key to continue...\n");
            getch();
            system("CLS");

            menu();
            fclose(log);
        }

    }
    system("CLS");
    printf("\nPlease enter correct user id or password...!\n");
    getch();
    fclose(log);
    fflush(stdin);
    system("CLS");
}
admenu()
{
    logo();
    int n;
    printf("\n\n\t1)Food Order Service\n");
    printf("\t2)Payment\n\n\n");
    printf("\tEnter your choice:- ");
    scanf("%d",&n);
    switch(n)
    {
    case 1:
        admfood();
        break;
    case 2:
        adpayment();
        break;
    }
     getch();
    system("CLS");
}
admfood()
{
    system("CLS");
    logo();
    printf("\n\n\n");
    int n;
    printf("1)Check available food items\n");
    printf("2)Add food items\n");
    printf("3)Update food item\n\n\n");
    printf("Enter your choice:- ");
    scanf("%d",&n);
    switch(n)
    {
    case 1:
        system("CLS");
        logo();
        printf("\n\n\n");
        adview();
        break;
    case 2:
        system("CLS");
        logo();
        printf("\n\n\n");
        int a;
        printf("Press 1 for breakfast\n");
        printf("Press 2 for lunch\n");
        printf("Press 3 for dinner\n");
        printf("Enter your choice:- \n");
        scanf("%d",&a);
        switch(a)
        {
        case 1:
             system("CLS");
            adbreakfast();
            break;
        case 2:
             system("CLS");
            adlunch();
            break;
        case 3:
             system("CLS");
            addinner();
            break;
        }
        break;
    case 3:
        adupdate();
        break;
    }
}
struct fod
{
    char name[30];
    int price[20];
};
adfood()
{
    int c;
    printf("Press 1 for add breakfast\n");
    printf("Press 2 for add lunch\n");
    printf("Press 3 for add dinner\n");
    printf("Enter your choice:- \n");
    scanf("%d",&c);
    if(c==1)
    {
        adbreakfast();
    }
    else if(c==2)
    {
        adlunch();
    }
    else if(c==3)
    {
        addinner();
    }
    else{
        adfood();
    }
}
adview()
{
    logo();
    printf("\n\n\n");
    struct fod m;
    FILE*fp;
    fp=fopen("food.txt","r");
    printf("Name:- ",m.name);
    printf("Price:- ",m.price);
    fwrite(&m,sizeof(m),1,fp);
    fclose(fp);
    fflush(stdin);
}
adupdate()
{
    logo();
    printf("\n\n\n");
    char another;
    struct fod a;
    char nm[20];
    int c,b;
    FILE *fp;
    fp=fopen("food.txt","r+");
    fflush(stdin);
    system("CLS");
    another= 'y';
    while(another == 'y')
    {
        printf("\nEnter name: ");
        scanf("%s",&nm);
        rewind(fp);

        while(fread(&a,sizeof(a),1,fp)==1)
        {
            if(strcmp(a.name,nm)==0)
            {
                Sleep(100);
                printf("Press 1 for update breakfast\n");
                Sleep(100);
                printf("Press 2 for update lunch\n");
                Sleep(100);
                printf("Press 2 for update dinner\n");
                Sleep(100);
                printf("Enter your choice:- \n");
                c=getche();
                switch(c)
                {
                case '1':
                    system("CLS");
                   adbreakfast();
                   break;
                case '2':
                    system("CLS");
                   adlunch();
                   break;
                case '3':
                    system("CLS");
                    addinner();
                    break;
                }
                fwrite(&a,sizeof(a),1,fp);
                break;
            }
            else
            {
                printf("\nNot match the information\n");
                break;
            }
        }
        printf("\nModify another record(y/n)");
        another=getch();
    }
    fclose(fp);
    fflush(stdin);
     printf("\n1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&b);
    switch(b)
    {
    case 1:
        system("CLS");
        menu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    }
}
logo()
{
    gotoxy (59,0);
    printf("%c",201);
    gotoxy (59,1);
    printf("%c",186);
    gotoxy (97,1);
    printf("%c",186);
     gotoxy (59,2);
    printf("%c",200);

    gotoxy (60,0);
    printf("%c",205);
    gotoxy (61,0);
    printf("%c",205);
    gotoxy (62,0);
    printf("%c",205);
    gotoxy (63,0);
    printf("%c",205);
    gotoxy (64,0);
    printf("%c",205);
    gotoxy (65,0);
    printf("%c",205);
    gotoxy (66,0);
    printf("%c",205);
    gotoxy (67,0);
    printf("%c",205);
    gotoxy (68,0);
    printf("%c",205);
    gotoxy (69,0);
    printf("%c",205);
    gotoxy (70,0);
    printf("%c",205);
    gotoxy (71,0);
    printf("%c",205);
    gotoxy (72,0);
    printf("%c",205);
    gotoxy (73,0);
    printf("%c",205);
    gotoxy (74,0);
    printf("%c",205);
    gotoxy (75,0);
    printf("%c",205);
    gotoxy (76,0);
    printf("%c",205);
    gotoxy (77,0);
    printf("%c",205);
    gotoxy (78,0);
    printf("%c",205);
    gotoxy (79,0);
    printf("%c",205);
    gotoxy (80,0);
    printf("%c",205);
    gotoxy (81,0);
    printf("%c",205);
    gotoxy (82,0);
    printf("%c",205);
    gotoxy (83,0);
    printf("%c",205);
    gotoxy (84,0);
    printf("%c",205);
    gotoxy (85,0);
    printf("%c",205);
    gotoxy (86,0);
    printf("%c",205);
    gotoxy (87,0);
    printf("%c",205);
    gotoxy (88,0);
    printf("%c",205);
    gotoxy (89,0);
    printf("%c",205);
    gotoxy (90,0);
    printf("%c",205);
    gotoxy (91,0);
    printf("%c",205);
    gotoxy (92,0);
    printf("%c",205);
    gotoxy (93,0);
    printf("%c",205);
    gotoxy (94,0);
    printf("%c",205);
    gotoxy (95,0);
    printf("%c",205);
    gotoxy (96,0);
    printf("%c",205);
    gotoxy (97,0);
    printf("%c",187);

    gotoxy (60,2);
    printf("%c",205);
    gotoxy (61,2);
    printf("%c",205);
    gotoxy (62,2);
    printf("%c",205);
    gotoxy (63,2);
    printf("%c",205);
    gotoxy (64,2);
    printf("%c",205);
    gotoxy (65,2);
    printf("%c",205);
    gotoxy (66,2);
    printf("%c",205);
    gotoxy (67,2);
    printf("%c",205);
    gotoxy (68,2);
    printf("%c",205);
    gotoxy (69,2);
    printf("%c",205);
    gotoxy (70,2);
    printf("%c",205);
    gotoxy (71,2);
    printf("%c",205);
    gotoxy (72,2);
    printf("%c",205);
    gotoxy (73,2);
    printf("%c",205);
    gotoxy (74,2);
    printf("%c",205);
    gotoxy (75,2);
    printf("%c",205);
    gotoxy (76,2);
    printf("%c",205);
    gotoxy (77,2);
    printf("%c",205);
    gotoxy (78,2);
    printf("%c",205);
    gotoxy (79,2);
    printf("%c",205);
    gotoxy (80,2);
    printf("%c",205);
    gotoxy (81,2);
    printf("%c",205);
    gotoxy (82,2);
    printf("%c",205);
    gotoxy (83,2);
    printf("%c",205);
    gotoxy (84,2);
    printf("%c",205);
    gotoxy (85,2);
    printf("%c",205);
    gotoxy (86,2);
    printf("%c",205);
    gotoxy (87,2);
    printf("%c",205);
    gotoxy (88,2);
    printf("%c",205);
    gotoxy (89,2);
    printf("%c",205);
    gotoxy (90,2);
    printf("%c",205);
    gotoxy (91,2);
    printf("%c",205);
    gotoxy (92,2);
    printf("%c",205);
    gotoxy (93,2);
    printf("%c",205);
    gotoxy (94,2);
    printf("%c",205);
    gotoxy (95,2);
    printf("%c",205);
    gotoxy (96,2);
    printf("%c",205);
    gotoxy (97,2);
    printf("%c",188);
    gotoxy(63,1);
    printf("ONLINE FOOD ORDER SERVICE");
}
start()
{
    logo();
    char ui[10],pw[10];
    int n;
    system("CLS");
    logo();
    printf("\n\n\n\n");
    printf("\nPress '1' for registration\n\nPress '2' for login\n\n\n");
    printf("Enter your choice:- ");
    scanf("%d",&n);
    switch(n)
    {
    case 1:
        system("CLS");
        logo();
        printf("\n\n\n\n");
        printf("\t\t\tREGISTRATION\n\t\t\t--------------\n\n\n");
        reg();
        break;
    case 2:
        system("CLS");
        login();
        break;
    }
    system("CLS");
}
menu()
{
    logo();
    printf("\n\n\n\n");
    int n,a,b;
    printf("\n\n\t1)Order Food\n");
    printf("\t2)Payment\n\n\n");
    printf("\tEnter your choice:- ");
    scanf("%d",&n);
    switch(n)
    {
    case 1:
        printf("Press 1 for breakfast\n");
        printf("Press 2 for lunch\n");
        printf("Press 3 for dinner\n");
        printf("Enter your choice:- \n");
        scanf("%d",&a);
        switch(a)
        {
        case 1:
            breakfast();
            printf("Press 1 for order\n");
            printf("Press 0 for exit\n");
            scanf("%d",&b);
            switch(b)
            {
            case 1:
                csinfo();
                break;
            case 0:
                exit(0);
                break;
            }
            break;
        case 2:
            lunch();
            printf("Press 1 for order\n");
            printf("Press 0 for exit\n");
            scanf("%d",&b);
            switch(b)
            {
            case 1:
                csinfo();
                break;
            case 0:
                exit(0);
                break;
            }
            break;
        case 3:
            dinner();
            printf("Press 1 for order\n");
            printf("Press 0 for exit\n");
            scanf("%d",&b);
            switch(b)
            {
            case 1:
                csinfo();
                break;
            case 0:
                exit(0);
                break;
            }
            break;
        }
        break;
    case 2:
        payment();
        break;
    }
    getch();
    system("CLS");
}
struct pay
{
    int a,cn,accn,pass,am;
    char fr;
};
payment()
{
    system("CLS");
    logo();
    printf("\n\n\n\n");
    printf("\t\t\tPAYMENT\n\t\t\t-------\n");
    int a,cn,accn,pass,am;
    char fr;
    struct fod b;
    FILE *fp;
    fp=fopen("payment.txt","w");
    printf("Do you want to pay with online\npress '1'\n");
    printf("Enter your choice:- ");
    a=getche();
    if(a=='1')
    {
        printf("For(Breakfast/Lunch/Dinner)\n");
        scanf("%s",&fr);
        printf("Card number:- ");
        scanf("%d",&cn);
        printf("account number:- ");
        scanf("%d",&accn);
        printf("Password:- ");
        scanf("%d",&pass);
        printf("Amount:- ");
        if(b.price==am)
        {
            scanf("%d",&am);
        }
        getch();
        system("CLS");
        logo();
        printf("\n\n\n\n");
        Sleep(100);
        printf("Your payment is successfully done.\n");
        Sleep(100);
        printf("Thanks for co-operating with us..\n");
    }
    else
    {
        Sleep(100);
        printf("You press wrong number. \n");
        Sleep(100);
        printf("please input correct one");
    }
    fclose(fp);
    fflush(stdin);
     printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        menu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;

    }
}
adpayment()
{
    system("CLS");
    logo();
    printf("\n\n\n\n");
    printf("\t\t\tPAYMENT\n\t\t\t-------\n");
    int a,cn,accn,pass,am;
    char fr;
    struct pay l;
    FILE *fp;
    fp=fopen("payment.txt","r");
    rewind(fp);
        Sleep(100);
        printf("For %s\n",l.fr);
        Sleep(100);
        printf("Card number:- %d\n",l.cn);
        Sleep(100);
        printf("account number:- %d\n",l.accn);
        Sleep(100);
        printf("Password:- %d\n",l.pass);
        Sleep(100);
        printf("Amount:- %d\n",l.am);
        getch();
        fread(&l,sizeof(l),1,fp);
    fclose(fp);
    fflush(stdin);
}
csinfo()
{
    system("CLS");
    logo();
    printf("\n\n\n\n");
    char na[10],em[20],ph[15],fr[10],lc[20],ti[10];
    printf("Name:- ");
    scanf("%s",&na);
    printf("Email:- ");
    scanf("%s",&em);
    printf("Phone:- ");
    scanf("%s",&ph);
    printf("For (Office/Home):- ");
    scanf("%s",&fr);
    printf("Location:- ");
    scanf("%s",&lc);
    printf("Time:- ");
    scanf("%s",&ti);
    getch();
    system("CLS");
    logo();
    printf("\n\n\n\n");
    Sleep(100);
    printf("Success fully done!!\n");
    Sleep(100);
    printf("Thanks for co-operating with us..\n");
}
adbreakfast()
{
    int a;
    struct fod m;
    FILE*abf;
    abf=fopen("breakfast.txt","a");
    printf("Enter the food name:- ");
    scanf("%s",&m.name);
    fprintf(abf,"%s",m.name);
    printf("Enter the food price:- ");
    scanf("%d",&m.price);

    fwrite(&m,sizeof(m),1,abf);

    fflush(stdin);
    fclose(abf);
    printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        admenu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        adbreakfast();
        break;
    }
}
adlunch()
{
    int a;
    struct fod m;
    FILE*fp;
    fp=fopen("lunch.txt","a");
    printf("Enter the food name:- \n");
    scanf("%s",&m.name);
    printf("Enter the food price:- \n");
    scanf("%d",&m.price);
    fwrite(&m,sizeof(m),1,fp);
    fclose(fp);
    fflush(stdin);
    printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        admenu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        adlunch();
        break;
    }
}
addinner()
{
    int a;
    struct fod m;
    FILE*fp;
    fp=fopen("dinner.txt","a");
    printf("Enter the food name:-");
    scanf("%s",&m.name);
    printf("Enter the food price:-");
    scanf("%d",&m.price);
    fwrite(&m,sizeof(m),1,fp);
    fclose(fp);
    fflush(stdin);
    printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        admenu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        addinner();
        break;
    }
}
breakfast()
{
    int a;
    struct fod m;
    FILE*fp;
    fp=fopen("breakfast.txt","r");
    printf("Enter the food name:-%s \n",m.name);
    printf("Enter the food price:-%d \n",m.price);
    fclose(fp);
    fflush(stdin);

        printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        menu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        breakfast();
        break;
    }
}
lunch()
{
    int a;
    struct fod m;
    FILE*fp;
    fp=fopen("lunch.txt","r");
    printf("Enter the food name:-%s \n",m.name);
    printf("Enter the food price:-%d \n",m.price);
    fread(&m,sizeof(m),1,fp);
    fclose(fp);
    fflush(stdin);
        printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        menu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        lunch();
        break;
    }
}
dinner()
{
    int a;
    struct fod m;
    FILE*fp;
    fp=fopen("dinner.txt","r");
    printf("Enter the food name:-%s \n",m.name);
    printf("Enter the food price:-%d \n",m.price);
    fread(&m,sizeof(m),1,fp);
    fclose(fp);
    fflush(stdin);
        printf("1)Main menu\n");
    printf("0)Exit\n");
    printf("Enter your choice:-\n");
    scanf("%d",&a);
    switch(a)
    {
    case 1:
        system("CLS");
        menu();
        break;
    case 0:
        system("CLS");
        exit(0);
        break;
    default:
        dinner();
        break;
    }
}
