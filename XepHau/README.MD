# XẾP HẬU

> THỰC HIỆN: VÕ XUÂN KHANG

```
#include <stdio.h>

int a[20],n=8,b[40],c[40],d[20];

void khoitao()
{
    for(int i = 0;i<n;i++)
    {
        d[i]=1;
    }
    for(int i = 2;i<2*n;i++)
    {
        b[i]=1;
    }
    for(int i = 1-n ; i < n-1 ; i++)
    {
        c[i]=1;
    }
}

void xuat()
{
    for(int i = 0 ; i < n ; i++)
    {
        printf("{%d%d} ",i,a[i]);
    }
}

void tim(int i)
{
    for(int j = 0 ; j < n ; j++)
    {
        if(d[j]&&b[i+j]&&c[i-j])
        {
            d[j]=b[i+j]=c[i-j]=0;
            a[i]=j;
            if(i==n)
            {
                xuat();
            }
            else
            {
                tim(i+1);
            }
            d[j]=b[i+j]=c[i-j]=1;
        }
    }
}

int main()
{
    khoitao();
    tim(1);
    return 0;
}
```
