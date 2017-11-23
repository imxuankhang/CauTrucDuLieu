# TÌM KIẾM NHỊ PHÂN

> THỰC HIỆN: VÕ XUÂN KHANG

```
#include <stdio.h>
int timkiemnhiphan(int a[], int dau, int cuoi, int gttim)
{
    int i = (dau+cuoi)/2;
    int x = a[i];
    if(gttim<x)
    {
        timkiemnhiphan(a,dau,i-1,gttim);
    }
    else if(gttim>x)
    {
        timkiemnhiphan(a,i+1,cuoi,gttim);
    }
    else
        return i;
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
            if(i<j)
            {
                temp=a[i];
                a[i]=a[j];
                a[j]=a[i];
            }
            i++;
            j--;
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
    printf("Nhap n:");
    scanf("%d",&n);
    for(int i = 0 ; i < n ; i++)
    {
        printf("Nhap a[%d]:",i);
        scanf("%d",&a[i]);
    }
    quicksort(a,0,n-1);
    for(int i = 0 ; i < n ; i++)
    {
        printf("%d  ",a[i]);
    }
    int gttim;
    printf("\nnhap gia tri can tim:");
    scanf("%d",&gttim);
    int x = timkiemnhiphan(a,0,n-1,gttim);
    printf("%d",x);
    return 0;
}

```
