Merge Sort :
# include <stdio.h>
# include <time.h>
#include <conio.h>
#include<stdlib.h>
int a[100000],b[100000];
void merge(int l,int m,int h)
{
int i,j,k;
i=l; j=m+1; k=l;
while(i<=m && j<=h)
{
if( a[i] <a[j])
{ b[k]=a[i]; i++; }
else
{ b[k]=a[j]; j++; }
k++;
}
while ( i<=m)
{
b[k]=a[i]; k++; i++;
}
while(j<=h)
{
b[k]=a[j]; k++; j++;
}
for(i=l;i<=h;i++)
a[i]=b[i];
}
void mergesort(int l,int h)
{
if(l<h)
{
int m=(l+h)/2;
mergesort(l,m);
mergesort(m+1,h);
merge(l,m,h);
}
}
main()
{
int i,j,n,k;
clock_t s,e;
double TT;
printf("\n Enter number of elements \n");
scanf("%d",&n);
for(i=0;i<n;i++)
{
a[i]=rand();
//a[i]=i;
//a[i]=n-i;
}
printf("\n UNSORTED ARRAY \n");
for(i=0;i<n;i++)
printf("%d\t",a[i]);
k=n/2;
s=clock();
mergesort(1,k);
mergesort(k+1,n);
merge(1,k,n);
e=clock();
printf("\n SORTED ARRAY \n");
for(i=0;i<n;i++)
printf("%d\t",a[i]);
printf("\n\n");
TT = ((double)(e - s)) / CLOCKS_PER_SEC;
printf("Time taken to sort %d elements: %lf seconds\n", n, TT);
}
