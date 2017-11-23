# CỘNG 2 ĐA THỨC 

> THỰC HIỆN: VÕ XUÂN KHANG

```
#include <stdio.h>
struct NODE
{
    int heso;
    int somu;
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

NODE* taonode(int heso,int somu)
{
    NODE *p = new NODE;
    p->heso=heso;
    p->somu=somu;
    p->pNext=NULL;
    return p;
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

void nhap(LIST &l)
{
    int n,heso,i;
    printf("\nNhap bac cua da thuc:");
    scanf("%d",&n);
    for(i = n;i>=0;i--)
    {
        printf("Nhap he so cua x^%d:",i);
        scanf("%d",&heso);
        NODE *p = taonode(heso,i);
        themcuoi(l,p);
    }
}

void xuat(LIST l)
{
    NODE *p = l.pHead;
    while(p!=NULL)
    {
        printf("%dX^%d",p->heso,p->somu);
        if(p->pNext!=NULL)
        {
            if(p->pNext->heso>=0)
                printf("+");
            else
                printf("");
        }
        p=p->pNext;
    }
}

void cong(LIST &l,LIST l1,LIST l2)
{
    NODE *p = new NODE;
    NODE *q = new NODE;
    //gan l = max(l1,l2) va p=lmin.pHead
    if((l1.pHead->somu) > (l2.pHead->somu))
    {
        l=l1;
        p=l2.pHead;
    }
    else
    {
        l=l2;
        p=l1.pHead;
    }
    q=l.pHead;
    //tim q sao cho q->somu = p->somu
    while(q->somu > p->somu)
    {
        q=q->pNext;
    }
    //cong 2 he so cung so mu
    while(q!=NULL)
    {
        q->heso+=p->heso;
        q=q->pNext;
        p=p->pNext;
    }
}
```
int main()
{
    LIST l1,l2;
    khoitao(l1);
    khoitao(l2);
    nhap(l1);
    xuat(l1);
    nhap(l2);
    xuat(l2);
    LIST l;
    khoitao(l);
    cong(l,l1,l2);
    printf("\n===========Cong 2 da thuc=============\n");
    xuat(l);
    return 0;
}

