# circular-linked-list
code for circular linked list

#include<stdio.h>
#include<stdlib.h>

struct clist
{
    int info;
    struct clist* next;

};
struct clist *start=NULL;

void add(int item)
{
    struct clist *ptr1,*ptr2;
    if (start==NULL)
    {
        start=(struct clist* )malloc(sizeof(struct clist));
        start->info=item;
        start->next=start;
    }
    else
    {
        ptr1=start;
        while(ptr1->next!=NULL)
        {
            ptr1=ptr1->next;
        }
        ptr2= (struct clist*)malloc(sizeof(struct clist));
        ptr1->next=ptr2;
        ptr2->next=start;
        ptr2->info=item;

    }
}

int delete()
{
    int item=0;
    struct clist *ptr1,*ptr2;
    ptr1=start;
    start=ptr1->next;
    while(ptr2!=NULL)
    {
        ptr2=ptr2->next;
    }
    free(ptr1);

    return item;
}

void show()
{
    struct clist*ptr1;
    ptr1=start;
    printf("START->");
    while (ptr1!=NULL)
    {
        printf("%d->", ptr1->info);
        ptr1=ptr1->next;
    }
    printf("NULL");
}

void main()
{
     int op,val;
    do
    {
        printf("\nDouble linked operations");
        printf("\n1. ADD ");
        printf("\n2. Delete");
        printf("\n3. SHOW");
        printf("\n0. EXIT");
        printf("\nEnter the choice : ");
        scanf("%d",&op);
        if(op==0) break;
        else if(op==1)
        {
            printf("Enter the number to be inserted : ");
            scanf("%d",&val);
            add(val);
            printf("Added  \n");
        }
        else if(op==2)
        {
            val=delete();
            printf("Item deleted=%d", val);
        }

        else if(op==3)
        {
            show();
        }

    }while(1);
}

