# contact-management-system-using-linked-list

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
struct contact
{
    char name[100];
    char phono[15];
    struct contact *next;
};
struct contact *head = NULL;
void toadd();
void display();
void search();
void delete();
void count();
int main()
{
    int choice;
    while (1)
    {
        printf("=====CONTACTS=====\n");
        printf("1) ADD CONTACT\n");
        printf("2) DISPLAY ALL CONTACT\n");
        printf("3) SEARCH CONTACT\n");
        printf("4) DELETE CONTACT\n");
        printf("5) COUNT NUMBER OF CONTACT\n");
        printf("0) EXIT\n");
        scanf("%d",&choice);
        switch(choice)
        {
            case 1:
                toadd();
                break;
           case 2:
                display();
                break; 
           case 3:
                search();
                break;
           case 4:
                delete();
                break; 
           case 5 :
                count();
                break;
           case 0 :
                printf("=====PROGRAM EXIT=====\n");
                exit(0);
                break;
           default :
                printf("ENTER VALID NUMBER\n");
                break;  
        }
    }
}
void toadd()
{
    struct contact *newnode,*temp;
    newnode=(struct contact *)malloc(sizeof(struct contact));
    printf("ENTER NAME : ");
    scanf("%s", newnode->name);
    printf("ENTER NUMBER : ");
    scanf("%s", newnode->phono);
    newnode->next=NULL;
    if (head==0)
        head=newnode;
    else 
    {
        temp=head;
        while (temp->next!=NULL)
            temp=temp->next;
        temp->next=newnode;
    }
    printf("CONTACT ADDED SUCCESSFULLY\n");
}
void display()
{
    struct contact *temp;
    temp=head;
    if (temp==NULL)
    {
        printf("THERE IS NO CONTACT\n");
        return;
    }
    while (temp!=NULL)
    {
        printf("NAME : %s || NUMBER : %s\n",temp->name,temp->phono);
        temp=temp->next;
    }
}
void search()
{
    char ns[50];
    struct contact *temp = head;
    int found = 0;

    printf("Enter name to search: ");
    scanf(" %[^\n]", ns);   

    while (temp != NULL)
    {
        if (strcmp(temp->name, ns) == 0)
        {
            printf("NAME : %s || NUMBER : %s\n",
                   temp->name, temp->phono);
            found = 1;
            break;
        }
        temp = temp->next;
    }

    if (!found)
        printf("Contact not found\n");
}
void delete()
{
    struct contact *temp = head, *prev = NULL;
    char del[50];
    printf("Enter name to delete: ");
    scanf(" %[^\n]", del);
    while (temp != NULL && strcmp(temp->name, del)!=0)
    {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL)
    {
        printf("Contact not found\n");
        return;
    }
    if (prev == NULL)
        head = temp->next;     
    else
        prev->next = temp->next;
    free(temp);
    printf("Contact deleted successfully\n");
}
void count()
{
    struct contact *temp=head;
    int count=0;
    while(temp!=NULL)
    {
        count++;
        temp=temp->next;
    }
    printf("NUMBER OF CONTACT : %d\n",count);
}
```

## OUTPUT

<img width="1862" height="981" alt="1 out" src="https://github.com/user-attachments/assets/4d898e19-39fd-4ab0-904f-9e105a59465d" />

<img width="1856" height="700" alt="2 out" src="https://github.com/user-attachments/assets/ec372ed3-04de-4fb6-aed3-d7ae030208ed" />
