# SORT (Interchange,Selection,Insertion,Buble,Quick)

> Thực hiện: VÕ XUÂN KHANG

```
#include <stdio.h>
void nhap(int a[],int n)
{
    printf("Nhap so luong phan tu mang:");
    scanf("%d",&n);
    for(int i = 0;i<n;i++){
        printf("Nhap a[%d]:",i);
        scanf("%d",&a[i]);
    }
}
void xuat(int a[],int n)
{
    for(int i = 0;i<n;i++)
    {
        printf("%d  ",a[i]);
    }
}
void interchangesort(int a[],int n)
{
    for(int i = 0;i<n-1;i++){
        for( int j = i+1;j<n;j++){
            if(a[j]<a[i]){
                int temp = a[i];
                a[i]=a[j];
                a[j]=temp;
            }
        }
    }
}
void selectionsort(int a[],int n)
{
    int vtmin,tam;
    for(int i = 0;i<n-1;i++)
    {
        vtmin = i;
        for(int j =i+1;j<n;j++)
        {
            if(a[j]<a[i])
            {
                vtmin = j;
            }
        }
        tam = a[i];
        a[i]=a[vtmin];
        a[vtmin]=tam;
    }
}
void insertionsort(int a[],int n)
{
    int pos,tam;
    for(int i = 1;i<n;i++)//bat dau tu vi tri thu 2
    {
        tam=a[i];
        pos=i-1; //vi tri de chen x
        while(pos>=0&&a[pos]>tam) //khi vi tri chen chua phai la dau mang va phan tu truoc lon hon x
        {
            a[pos+1]=a[pos];    //doi phan tu o vi tri thay the ve sau
            pos--;              // giam pos
        }
        a[pos+1]=tam;             // khi pos ve dau mang hoac a[pos]>=x thi thay the x = a[pos+1] (+1 o day chi cho trg hop ve dau mang pos=-1)
    }
}
void bublesort(int a[],int n)
{
    for(int i = 0 ; i<n-1 ; i++)
    {
        for(int j = n-1 ; j>i ; j--)
        {
            if(a[j-1]>a[j])
            {
                int tam = a[j-1];
                a[j-1] = a[j];
                a[j] = tam;
            }
        }
    }
}
void quicksort(int a[],int dau,int cuoi)
{
    int i=dau,j = cuoi;
    int x,temp;
    x = a[(dau+cuoi)/2];
    while(i<j)
    {
            while(a[i]<x)
            {
                i++;
            }
            while(a[j]>x)
            {
                j--;
            }
            if(i<=j)
            {
                temp=a[i];
                a[i]=a[j];
                a[j]=a[i];
                i++;
                j--;
            }
    }
    if(dau<j)
    {
        quicksort(a,dau,j);
    }
    if(cuoi>i)
    {
        quicksort(a,i,cuoi);
    }
}

int main()
{
    int a[100];
    int n;
    nhap(a,n);
    xuat(a,n);
    return 0;
}
```
