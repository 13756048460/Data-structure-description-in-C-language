**顺序表**

```c
#include<stdio.h>

#define MAXSIZE 20

typedef int Status;
typedef int ElemType;

//定义线性表
typedef struct
{
	ElemType data[MAXSIZE];//存储数据元素  #define MAXSIZE 20
	int length;//线性表长度
}SqList;

//初始化
void InitList(SqList *L) 
{ 
    L->length=0;
}

//判断是否为空表
int ListEmpty(SqList L)
{ 
	if(L.length==0)
		return 1;
	else
		return 0;
}

//删除所有表内元素重置为空表
void ClearList(SqList *L)
{ 
    L->length=0;
}

//返回线性表内数据的个数
int ListLength(SqList L)
{
	return L.length;
}

//返回数据元素第i位的值
int GetElem(SqList L,int i)
{
    //判断线性表是否存在，不存在则返回0，存在则返回输入的第i个元素的值
    if(L.length==0 || i<1 || i>L.length)
            return 0;
    return L.data[i-1];
}

//查找元素e在线性表中的位置
int LocateElem(SqList L,ElemType e)
{
    int i;
    //判断表是否为空，空则返回0
    if (L.length==0)
            return 0;
    //定位元素
    for(i=0;i<L.length;i++)
    {
        //判断遍历到的元素是否等于e
        if (L.data[i]==e)
            break;
    }
    if(i>=L.length)
            return 0;
    //返回位置
    return i+1;
}

//第i个位置之前插入新的数据元素e
void ListInsert(SqList *L,int i,ElemType e)
{ 
	int k;
	if (L->length==MAXSIZE)  /* 顺序线性表已经满 */
		return ERROR;
	if (i<1 || i>L->length+1)/* 当i比第一位置小或者比最后一位置后一位置还要大时 */
		return ERROR;

	if (i<=L->length)        /* 若插入数据位置不在表尾 */
	{
		for(k=L->length-1;k>=i-1;k--)  /* 将要插入位置之后的数据元素向后移动一位 */
			L->data[k+1]=L->data[k];
	}
	L->data[i-1]=e;          /* 将新元素插入 */
	L->length++;
}
//删除L的第i个数据元素
void ListDelete(SqList *L, int i) 
{ 
    int k;
    if (L->length == 0)               /* 线性表为空 */
        return;
    if (i < 1 || i > L->length)         /* 删除位置不正确 */
        return;
    if (i < L->length)                /* 如果删除不是最后位置 */
    {
        for (k = i; k < L->length; k++) /* 将删除位置后继元素前移 */
            L->data[k - 1] = L->data[k];
    }
    L->length--;
}


//依次对线性表的每个数据元素输出
void ListTraverse(SqList L)
{
	int i;
    for(i=0;i<L.length;i++)
            printf("%d\t",L.data[i])
    printf("\n");
    return OK;
}
```

