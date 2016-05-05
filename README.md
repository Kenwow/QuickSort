# QuickSort
homework

#include <stdio.h>
#include<stdlib.h>
#include<time.h>

void QuickSort(int array[], int start, int end);
void change(int *a, int *b);

int main(void)
{
	int a[1000];
	int i, j = 100;
	clock_t start;
	clock_t finish;


	start = clock();
	while (j--)
	{
		srand(time(NULL));
		for (i = 0; i < 1000; i++)
		{
			a[i] = rand() % 1000;

		}
		QuickSort(a, 0, 999);
		
	}
	finish = clock();

	printf("对1000个随机数进行快速排序1次所用时间为%fs\n\n", (double)(finish - start) / 100000);


	start = clock();
	j = 1000;
	while (j--)
	{
		srand(time(NULL));
		for (i = 0; i < 100; i++)
		{
			a[i] = rand() % 100;

		}
		QuickSort(a, 0, 99);

	}
	finish = clock();

	printf("对100个随机数进行快速排序1次所用时间为%fs\n\n下面是进行对20个随机数快速排序的演示\n", (double)(finish - start) / 1000000);


	
	srand(time(NULL));
	for (i = 0; i < 20; i++)
	{
		a[i] = rand() % 20;
		printf("%d ", a[i]);

	}
	printf("\n");
	QuickSort(a, 0, 19);

	printf("排序的结果是:\n");
	for (i = 0; i < 20; i++)
	{
		printf("%d ", a[i]);
	}
	printf("\n");
	
	printf("谢谢使用");
	return 0;
}
void QuickSort(int array[], int start, int end)
{
	int key;
	int i, j = end;
	key = array[end];

	if (end > start)
	{
		for (i = start; i < j; i++)
		{
			if (array[i] >= key)
			{
				while (i < j)
				{
					j--;
					if (array[j] < key)
						break;

				}
				change(&array[i], &array[j]);
			}
		}
		if (i > j)
			i--;
		change(&array[i], &array[end]);
		QuickSort(array, start, i - 1);
		QuickSort(array, i + 1, end);


	}
}

void change(int *a, int *b)
{
	int t;
	t = *a;
	*a = *b;
	*b = t;
}
