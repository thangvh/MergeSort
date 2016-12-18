# MergeSort
an algorithm

#include <stdio.h>

void Merge (int A[], int left, int mid, int right)
{
	int n1, n2;
	n1 = mid - left + 1;
	n2 = right - mid;
	
	int L[n1+1], R[n2+1];
	L[n1] = R[n2] = 1000;
	int i,j,k;
	for (i=0; i<n1; i++)
	    L[i] = A[left+i];
	for (i=0; i<n2; i++)  
	    R[i] = A[mid+1+i];
	i = j = 0;
	for (k=left; k<=right; k++)    
	{
		if (L[i] < R[j])
		    A[k] = L[i++];
		else
		   A[k] = R[j++];
	}
}

void MergeSort (int A[], int left, int right)
{
	if (left < right)
	{
		int mid = (left+right)/2;
		MergeSort (A, left, mid);
		MergeSort (A, mid+1, right);
		Merge (A, left, mid, right);
	}
}

int main()
{
  int A[] = {0, 1, 2, 1, 13, 6};
	int left, right;
	left = 0;    right = 5;
	MergeSort (A, left, right);
	
	for (int i=0; i<6; i++)
	    printf ("%d ",A[i]);
    
    return 0;
}
