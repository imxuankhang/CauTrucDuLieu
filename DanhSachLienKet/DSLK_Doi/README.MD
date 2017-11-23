# DANH SÁCH LIÊN KẾT ĐÔI

> THỰC HIỆN: VÕ XUÂN KHANG

```
#include <stdio.h>
struct NODE
{
    int data;
    NODE *pNext;
};

struct LIST
{
    NODE *pHead;
    NODE *pTail;
};

void khoitao(LIST &l)
{
    l.pHead=l.pTail=NULL;
}

NODE* taonode(LIST &l,int x)
{
    NODE *p = new NODE;
    p->data=x;
    p->pNext=NULL;
    return p;
}

void themdau(LIST &l,NODE *p)
{
    if(l.pHead==NULL)
    {
        l.pHead=l.pTail=p;
    }
    else
    {
        p->pNext=l.pHead;
        l.pHead=p;
    }
}

void themcuoi(LIST &l,NODE *p)
{
    if(l.pHead==NULL)
    {
        l.pHead=l.pTail=p;
    }
    else
    {
        l.pTail->pNext=p;
        l.pTail=p;
    }
}

NODE* timkiem(LIST &l,int timkiem)
{
    if(l.pHead==NULL)
        return NULL;
    else
    {
        NODE *q = l.pHead;
        while((q!=NULL)&&(q->data!=timkiem))
        {
            q=q->pNext;
        }
        return q;
    }
}

void themsauq(LIST &l,NODE *p,int giatritruocvitrichennode)
{
    NODE *q = timkiem(l,giatritruocvitrichennode);
    p->pNext=q->pNext;
    q->pNext=p;
}
void nhapthemsauq(LIST &l)
{
    int x,gttruocchen;
    printf("\nNhap gia tri node them vao:");
    scanf("%d",&x);
    NODE *p = taonode(l,x);
    printf("\nNhap gia tri truoc node them vao:");
    scanf("%d",&gttruocchen);
    themsauq(l,p,gttruocchen);
}

void xoadau(LIST &l)
{
    NODE *nodexoa = l.pHead;
    l.pHead=l.pHead->pNext;
    delete nodexoa;
}

void xoacuoi(LIST &l)
{
    NODE *nodexoa = l.pTail;
    NODE *q = l.pHead;
    //tim node truoc pTail
    while(((q->pNext)->pNext!=NULL)&&((q->pNext->data)!=(l.pTail->data)))
    {
        q=q->pNext;
    }
    l.pTail=q;
    l.pTail->pNext=NULL;
    delete nodexoa;
}

void nhapxoaq(LIST &l)
{
    int gtnodexoa;
    printf("\nNhap gia tri node can xoa:");
    scanf("%d",&gtnodexoa);
    NODE *nodexoa = timkiem(l,gtnodexoa);
    if(nodexoa==NULL)
    {
        printf("null");
    }
    else
    {
        NODE *q = l.pHead;
        while((q->pNext)->data!=nodexoa->data)
        {
            q=q->pNext;
        }
        q->pNext=q->pNext->pNext;
        delete nodexoa;
    }
}

void nhap(LIST &l)
{
    int n,x,i;
    NODE *p;
    printf("Nhap so node can tao:");
    scanf("%d",&n);
    for(i = 0 ; i < n ; i++)
    {
        printf("\nNhap gia tri node %d can tao:",i);
        scanf("%d",&x);
        p = taonode(l,x);
        themcuoi(l,p);
    }
}

void xuat(LIST l)
{
    NODE *p = l.pHead;
    printf("pHead-->");
    while(p!=NULL)
    {
        printf("%d-->",p->data);
        p=p->pNext;
    }
    printf("NULL");
}

int main()
{
    LIST l;
    khoitao(l);
    nhap(l);
    xuat(l);
    //nhapthemsauq(l);
    //xuat(l);
    /*int tim;
    printf("\nGia tri node can tim:");
    scanf("%d",&tim);
    NODE *q = timkiem(l,tim);
    if(q==NULL)
    {
        printf("NULL");
    }
    else
    {
        printf("%d",q->data);
    }*/
    //xoadau(l);
    //xoacuoi(l);
    //xuat(l);
    //printf("\n");
    nhapxoaq(l);
    xuat(l);
    nhapxoasauq(l);
    xuat(l);
    return 0;
}
```
