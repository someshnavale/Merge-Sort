# Merge-Sort

C Merge Sort

int merge(int arr[],int l,int m,int h)
{
 int arr1[10],arr2[10]; // Two temporary arrays to
 hold the two arrays to be merged
 int n1,n2,i,j,k;
 n1=m-l+1;
 n2=h-m;
 for(i=0; i<n1; i++)
 arr1[i]=arr[l+i];
 for(j=0; j<n2; j++)
 arr2[j]=arr[m+j+1];
 arr1[i]=9999; // To mark the end of each temporary array
 arr2[j]=9999;
 i=0;
 j=0;
 for(k=l; k<=h; k++) { //process of combining two sorted arrays
 if(arr1[i]<=arr2[j])
 arr[k]=arr1[i++];
 else
 arr[k]=arr2[j++];
 }
 return 0;
}
int merge_sort(int arr[],int low,int high)
{
 int mid;
 if(low<high) {
 mid=(low+high)/2;
 // Divide and Conquer
 merge_sort(arr,low,mid);
 merge_sort(arr,mid+1,high);
 // Combine
 merge(arr,low,mid,high);
 }
 return 0;
}

#Merge Sort Implementation in Java

public interface InPlaceSort<T extends Comparable<T>> {
void sort(final T[] elements); }
public class MergeSort < T extends Comparable < T >> implements InPlaceSort < T > {
@Override
public void sort(T[] elements) {
 T[] arr = (T[]) new Comparable[elements.length];
 sort(elements, arr, 0, elements.length - 1);
}
// We check both our sides and then merge them
private void sort(T[] elements, T[] arr, int low, int high) {
 if (low >= high) return;
 int mid = low + (high - low) / 2;
 sort(elements, arr, low, mid);
 sort(elements, arr, mid + 1, high);
 merge(elements, arr, low, high, mid);
}
private void merge(T[] a, T[] b, int low, int high, int mid) {
 int i = low;
 int j = mid + 1;
 // We select the smallest element of the two. And then we put it into b
 for (int k = low; k <= high; k++) {
 if (i <= mid && j <= high) {
 if (a[i].compareTo(a[j]) >= 0) {
 b[k] = a[j++];
 } else {
 b[k] = a[i++];
 }
 } else if (j > high && i <= mid) {
 b[k] = a[i++];
 } else if (i > mid && j <= high) {
 b[k] = a[j++];
 }
 }
 for (int n = low; n <= high; n++) {
 a[n] = b[n];
 }}}
