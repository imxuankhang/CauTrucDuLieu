# CÂY NHỊ PHÂN

> Thực hiện: VÕ XUÂN KH
```
/*
- KHAI BAO CAU TRUC CAY NHI PHAN
- KHOI TAO CAY
- THEM NUT X VAO CAY NHI PHAN
- NHAP DU LIEU
- DUYET CAY
*/
// CAY NHI PHAN TIM KIEM KO XUAT HIEN CAC PHAN TU TRUNG NHAU

#include <stdio.h>
struct NODE
{
    int data;
    NODE *pLeft;
    NODE *pRight;
};
typedef struct NODE *tree;

void khoitao(tree &t)
{
    t = NULL;
}

bool themnodevaocay(tree &t,int x)
{
    if(t==NULL)
    {
        if(x==NULL)
            return false;
        else
        {
            t = new NODE;
            t->data = x;
            t->pLeft = NULL;
            t->pRight = NULL;
            return true;
        }
    }
    else
    {
        if(x<t->data)
            themnodevaocay(t->pLeft,x);
        else
            themnodevaocay(t->pRight,x);
    }
}

void nhapdulieu(tree &t)
{
    int x;
    khoitao(t);
    do
    {
        printf("Nhap gia tri x cho node(nhap 0 de ket thuc):");
        scanf("%d",&x);
        if(x==0)
            break;
        else
            themnodevaocay(t,x);
    }
    while(true);
}

void DuyetLNR(tree t)
{
    if(t!=NULL)
    {
        DuyetLNR(t->pLeft);
        printf("%d ",t->data);
        DuyetLNR(t->pRight);
    }
}

void DuyetLRN(tree t)
{
    if(t!=NULL)
    {
        DuyetLRN(t->pLeft);
        DuyetLRN(t->pRight);
        printf("%d ",t->data);
    }
}

void DuyetNLR(tree t)
{
    if(t!=NULL)
    {
        printf("%d ",t->data);
        DuyetNLR(t->pLeft);
        DuyetNLR(t->pRight);
    }
}

NODE* timkiem(tree t,int tim)
{
    if(t==NULL)
        return NULL;
    else if (tim<t->data)
        timkiem(t->pLeft,tim);
    else
    {
        if(tim>t->data)
            timkiem(t->pRight,tim);
        else
            return t;
    }
}

//Neu nut xoa la nut la => xoa binh thuong
//Neu nut xoa la nut co 1 con => moc nut con cua no len va xoa bth
//Neu nut xoa la nut co 2 con => tim phan tu the mang: + chon nut trai nhat cay con phai hoac chon nut phai nhat cay con trai
void xoanut(tree &t,int y)
{
    if(t!=NULL)
    {
        if(y<t->data)
            xoanut(t->pLeft,y);
        else if(y>t->data)
            xoanut(t->pRight,y);
        else
        {
            NODE *p = t;
            if(t->pLeft==NULL)
                t=t->pRight;
            else if(t->pRight==NULL)
                t=t->pLeft;
            else
            {
                NODE* &q = t->pRight;
                while(q->pLeft!=NULL)
                {
                    q=q->pLeft;
                }
                p->data=q->data;
                p=q;
                q=q->pRight;
            }
            delete p;
        }
    }
}

int main()
{
    //int tim;
    NODE *p;
    tree t;
    nhapdulieu(t);
    printf("\nDuyet LNR:");
    DuyetLNR(t);
    printf("\nDuyet NLR:");
    DuyetNLR(t);
    printf("\nDuyet LRN:");
    DuyetLRN(t);
    //printf("\nNhap phan tu can tim:");
    //scanf("%d",&tim);
    //NODE *q = timkiem(t,tim);
    //if(q==NULL)
    //    printf("%d khong ton tai",tim);
    //else
    //    printf("%d ton tai trong cay nhi phan",tim);
    int y;
    printf("\nNhap nut can xoa:");
    scanf("%d",&y);
    xoanut(t,y);
    printf("\nDuyet LNR:");
    DuyetLNR(t);
    printf("\nDuyet NLR:");
    DuyetNLR(t);
    printf("\nDuyet LRN:");
    DuyetLRN(t);
    return 0;
}
```
