# HEAP SORT

> THỰC HIỆN: VÕ XUÂN KHANG

```
#include <stdio.h>
void nhap(int a[],int &n)
{
    printf("Nhap n:");
    scanf("%d",&n);
    for(int i = 0 ; i < n ; i++)
    {
        printf("Nhap a[%d]:",i);
        scanf("%d",&a[i]);
    }
}

void xuat(int a[],int n)
{
    for(int i = 0 ; i < n ; i++)
    {
        printf("%d  ",a[i]);
    }
}

void heap(int a[],int n,int vt)
{
    while(vt<=(n/2-1))
    {
        int con1 = vt*2+1;
        int con2 = vt*2+2;
        int tam = con1;
        if(con2<n&&(a[con2]>a[con1]))
        {
            tam=con2;
        }
        if(a[vt]<a[tam])
        {
            int temp = a[tam];
            a[tam] = a[vt];
            a[vt] = temp;
        }
        vt = tam;
    }
}
void buidheap(int a[],int n)
{
    for(int i = n/2-1 ; i>=0 ; i--)
    {
        heap(a,n,i);
    }
}

void heap_sort(int a[],int n)
{
    buidheap(a,n);
    for(int i = n-1 ; i>=0 ; i--)
    {
        int temp = a[i];
        a[i] = a[0];
        a[0] = temp;
        heap(a,i,0);
    }
}

int main()
{
    int a[100];
    int n;
    nhap(a,n);
    heap_sort(a,n);
    xuat(a,n);
    return 0;
}
```
