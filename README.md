//simple-projrct-in-c-
#include<stdlib.h>
#include<string.h>
#includ<stdio.h>
#include<windows.h>

struct Student
{
    int rollnumber;
    char namee[100];
    char phone[100];
    float percentage;
    struct Student *next;
    
}* head;


void login()
{
	
	int a=0,i=0;
    char uname[10],c=' '; 
    char pword[10],code[10];
    char user[]="DATA";
    char pass[10]="debian";
    do
{
	system("cls");
	setcolor(8);
	
	printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
	
    printf("\n\t\t\t\t\t\t\t  *********  LOGIN FORM  *********  ");
    printf(" \n\n\t\t\t\t\t\t\t                       ENTER USERNAME:-");
	scanf("%s", &uname); 
	printf(" \n\t\t\t\t\t\t\t                       ENTER PASSWORD:-");
	while(i<10)
	{
	    pword[i]=getch();
	    c=pword[i];
	    if(c==13) break;
	    else printf("*");
	    i++;
	}
	pword[i]='\0';
	//char code=pword;
	i=0;
	//scanf("%s",&pword); 
		if(strcmp(uname,"DATA")==0 && strcmp(pword,"debian")==0)
	{
	printf("  \n\n\n       WELCOME !!!! LOGIN IS SUCCESSFUL");
	
	break;
	}
	else
	{
		printf("\n        SORRY !!!!  LOGIN IS UNSUCESSFUL");
		a++;
	
		getch();

	}
}
	while(a<=2);
	if (a>2)
	{
		printf("\nSorry you have entered the wrong username and password for three times!!!");
		exit(0);
		getch();
		
		}
		system("cls");	
}


void setcolor(int ForgC)
{ WORD wColor;
HANDLE hStdOut=GetStdHandle(STD_OUTPUT_HANDLE);
CONSOLE_SCREEN_BUFFER_INFO csbi;

if(GetConsoleScreenBufferInfo(hStdOut,&csbi))
{
	wColor=(csbi.wAttributes & 0xB0)+(ForgC & 0x0B);
//	SetConsoleTextAttributes(hStdOut,wColor);
	SetConsoleTextAttribute(hStdOut,wColor);
	
}
}
void insert(int rollnumber, char* name, char* phone, float percentage)
{
    
    struct Student * student = (struct Student *) malloc(sizeof(struct Student));
    student->rollnumber = rollnumber;
    strcpy(student->name, name);
    strcpy(student->phone, phone);
    student->percentage = percentage;
    student->next = NULL;
    
    if(head==NULL){
        // if head is NULL
        // set student as the new head
        head = student;
    }
    else{
        // if list is not empty
        // insert student in beginning of head
        student->next = head;
        head = student;
    }
    
}
void search(int rollnumber)
{
    struct Student * temp = head;
    while(temp!=NULL){
        if(temp->rollnumber==rollnumber){
            printf("\n\n\t\t\t\t\t\tRoll Number: %d\n", temp->rollnumber);
            printf("\t\t\t\t\t\tName: %s\n", temp->name);
            printf("\t\t\t\t\t\tPhone: %s\n", temp->phone);
            printf("\t\t\t\t\t\tPercentage: %0.4f\n", temp->percentage);
            return;
        }
        temp = temp->next;
    }
    printf("\nStudent with roll number %d is not found !!!\n", rollnumber);
}
void update(int rollnumber)
{
    
    struct Student * temp = head;
    while(temp!=NULL){
        
        if(temp->rollnumber==rollnumber){
            printf("\nRecord with roll number %d Found !!!\n", rollnumber);
            printf("\n\nEnter new name: ");
            scanf("%s", temp->name);
            printf("Enter new phone number: ");
            scanf("%s", temp->phone);
            printf("Enter new percentage: ");
            scanf("%f",&temp->percentage);
            printf("Updation Successful!!!\n");
            return;
        }
        temp = temp->next;
        
    }
    printf("\nStudent with roll number %d is not found !!!\n", rollnumber);
    
}
void Delete(int rollnumber)
{
    struct Student * temp1 = head;
    struct Student * temp2 = head; 
    while(temp1!=NULL){
        
        if(temp1->rollnumber==rollnumber){
            
            printf("\nRecord with roll number %d Found !!!\n", rollnumber);
            
            if(temp1==temp2){
                // this condition will run if
                // the record that we need to delete is the first node
                // of the linked list
                head = head->next;
                free(temp1);
            }
            else{
                // temp1 is the node we need to delete
                // temp2 is the node previous to temp1
                temp2->next = temp1->next;
                free(temp1); 
            }
            
            printf("\nRecord Successfully Deleted !!!\n");
            return;
            
        }
        temp2 = temp1;
        temp1 = temp1->next;
        
    }
    printf("\nStudent with roll number %d is not found !!!\n", rollnumber);
    
}
void display()
{
	setcolor(15);
    struct Student * temp = head;
    while(temp!=NULL){
        printf("\t\t\t\t\t\t--------------------------------------\n");
        printf("\t\t\t\t\t\tRoll Number: %d                       \n", temp->rollnumber);
        printf("\t\t\t\t\t\tName: %s                              \n", temp->name);
        printf("\t\t\t\t\t\tPhone: %s                             \n", temp->phone);
        printf("\t\t\t\t\t\tPercentage: %0.4f                     \n", temp->percentage);
       printf("\t\t\t\t\t\t----------------------------------------\n");
        printf("\n\n\n\n\n");
        temp = temp->next;
        	
    }
}



void end()
{
	setcolor(8);
	system("cls");
	printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\t\t\t\t\t\t\t\t\t\tTHANK YOU\n");
	printf("\t\t\t\t\t\t\t\t\t\t BY TEAM \n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
    exit(0);
	system("cls");
}
int main()
{
	
	
printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\t\t\t\t\t\t\t\t\t\tLOADING......\n");
printf("\t\t\t\t\t\t\t\t\t\tPLEASE BE PATIENT");
	sleep(5);
	system("cls");


    
    head = NULL;
    int choice;
    char name[100];
    char phone[100];
    int rollnumber;
    float percentage;
    
    login();
    setcolor(6);
    
printf("\t\t\t\t\t\t\t\t DS PROJECT: PROGRAM ON STUDENTS RECORD MANAGEMENT SYSYEM\n\n");

    printf("\t\t\t      [[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]\n");
	printf("\t\t\t      |                                                                                                                             |\n");      
	printf("\t\t\t      |                                                                                                                             |\n");
	printf("\t\t\t      | W E L C O M E      W E L C O  W E L C  W E L C  W E L C O M E  W E L C O M E  W W       E  W E L C O M E      W E L C O M E |\n");
	printf("\t\t\t      | E                  E       M  E        E              W              W        E  E      M  E                  E             |\n");
	printf("\t\t\t      | L                  L       E  L        L              E              E        L   L     O  L                  L             |\n");
	printf("\t\t\t      | C     E M O C O M  C   L E W  C O M E  C O M E        L              L        C    C    C  C     E M O C O M  C O M E W E L |\n");
	printf("\t\t\t      | O           L   E  O    C     O        O              C              C        O     O   L  O           L   E              C |\n");
	printf("\t\t\t      | M           E      M     O    M        M              O              O        M      M  E  M           E                  O |\n");
	printf("\t\t\t      | E M O C L E W      E      M   E M O C  E M O C        M        W E L C O M E  E       E W  E M O C L E W      O C L E W E M |\n");                       
	printf("\t\t\t      |                                                                                                                             |\n");      
	printf("\t\t\t      |                                                                                                                             |\n");      
	printf("\t\t\t      [[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]\n\n\n\n");
 	
	 
	printf("\t\t\t\t\t\t\t\t  ________________\n");
	printf("\t\t\t\t\t\t\t\t||                                              ||\n");
	printf("\t\t\t\t\t\t\t\t||        ---------------------------------     ||\n");
	printf("\t\t\t\t\t\t\t\t||           CV RAMAN GLOBAL UNIVERSITY         ||\n");
	printf("\t\t\t\t\t\t\t\t||        ---------------------------------     ||\n");
	printf("\t\t\t\t\t\t\t\t||                                              ||\n");
	printf("\t\t\t\t\t\t\t\t||          SUBJECT TEACHER : MRS MAMTA         ||\n");
	printf("\t\t\t\t\t\t\t\t||                                              ||\n");
	printf("\t\t\t\t\t\t\t\t||             Brought To You By TEAM           ||\n");
	printf("\t\t\t\t\t\t\t\t||                                              ||\n");
	printf("\t\t\t\t\t\t\t\t||________________||\n\n\n");
	
	
	
	 printf("\t\t\t    NAME                       ROLL NO.      REG. NO         PHONE NO.              EMALI ID                   COLLEGE MAIL ID        \n\n");
	
	printf("\t\t\t  PRATIK KARN                 CSE20186      20010178        9866874127       pratikkarn48@gmail.com        20010178@cgu-odisha.ac.in      \n");
    printf("\t\t\t  ABNISH YADAV                CSE20185      20010177        9809636650      yadavabnish074@gmail.com       20010177@cgu-odisha.ac.in      \n");
	printf("\t\t\t  ISHAN MANDAL                CSE20191      20010791        9819910763       mandalishan96@gmail.com       20010791@cgu-odisha.ac.in      \n");
	printf("\t\t\t  MUNNA KUMAR KUSHWAHA        CSE20196      20010799        9819663559        munnakush0@gmail.com         20010799@cgu-odisha.ac.in      \n");	
	printf("\t\t\t  PIYUSH SINGH                CSE20197      20010801        8092461204      piyushsingh.4949@gmail.com     20010801@cgu-odisha.ac.in      \n");
	
    getch();
printf("Press any key to continue........");
system("cls");
int i;
setcolor(8);
		for(i=0;i<172;i++)
		printf("-");
	    printf("\n\t\t\t\t\t\t\t\t\t\t\tMAIN MENU\n");
	    for(i=0;i<172;i++)
		printf("-");
		setcolor(5);
		printf("\n");
    printf("\t\t\t\t\t\t\t\t\t ----------------------------------------\n"); 
    printf("\t\t\t\t\t\t\t\t\t|<1> Insert student details             |\n");
    printf("\t\t\t\t\t\t\t\t\t|<2> Search for student details         |\n");
    printf("\t\t\t\t\t\t\t\t\t|<3> Delete student details             |\n");
    printf("\t\t\t\t\t\t\t\t\t|<4> Update student details             | \n");
    printf("\t\t\t\t\t\t\t\t\t|<5> Display all student details        |\n");
    printf("\t\t\t\t\t\t\t\t\t|<6> EXIT                               |\n"); 
    printf("\t\t\t\t\t\t\t\t\t ---------------------------------------\n\n\n\n");

for(choice=0;choice<10;choice)
{



     setcolor(7);   
        printf("\n\n\t\t\t\t>>>>>>>Enter Choice: ");
        scanf("\t\t\t\t\t\t%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter roll number: ");
                scanf("%d", &rollnumber);
                printf("Enter name: ");
                scanf("%s", name);
                printf("Enter phone number: ");
                scanf("%s", phone);
                printf("Enter percentage: ");
                scanf("%f", &percentage);
                insert(rollnumber, name, phone, percentage);
                break;
            case 2:
                printf("\n\n\t\t\tEnter roll number to search: ");
                scanf("%d", &rollnumber);
                search(rollnumber);
                break;
            case 3:
                printf("\n\n\t\t\tEnter roll number to delete: ");
                scanf("%d", &rollnumber);
                Delete(rollnumber);
                break;
            case 4:
                printf("\n\n\t\t\tEnter roll number to update: ");
                scanf("%d", &rollnumber);
                update(rollnumber);
                break;
            case 5:
            printf("\n\n\t\t\tRecord Of The Students\n\n");
                display();
                break;
            
			case 6:
				end();
			break;
			    
            default:
            	printf("Invalid Choice");
            	break;
        }
        
} 

    system("cls");

}
