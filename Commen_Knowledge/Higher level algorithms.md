# 2.Higher level algorithms



### 1.The basic graph about the merge algorithm



![Merge\_sort\_animation2](\image\Merge\_sort\_animation2.gif)



**The key idea of the merge sort algorithm is using the trick that the two sub lists have already been sorted**

### code review

Using the recursive version of the merge sort algorithm.

```c++
//merge the two parts of the array: arr[l,...,mid] and arr[mid+1,...,r].
template <typename T>
void __merge(T arr[],int l,int mid,int r){

    T aux[r-l+1];

    for( int i = l;i <= r; i ++ )
        aux[i-l] = arr[i];

    int i = l,j = mid+1;
    for( int k = l;k <= r; k ++ ){
        //The first two ifs are the boundaries conditions.
        if( i > mid ){
            arr[k] = aux[j-l];
            j ++;
        }
        else if( j > r ){
            arr[k] = aux[i-l];
            i ++;
        }
        else if( aux[i-l] < aux[j-l] ){
            arr[k] = aux[i-l];
            i ++;
        }
        else{
            arr[k] = aux[j-l];
            j ++;
        }
    }
}

template <typename T>
void __mergeSort(T arr[],int l,int r){
    if( l >= r )
        return;
    int mid = l + (r-l)/2;
    __mergeSort(arr,l,mid);
    __mergeSort(arr,mid+1,r);
    __merge(arr,l,mid,r);
}

template <typename T>
void mergeSort(T arr[],int n){
    __mergeSort(arr,0,n-1);
}
```

原地归并的抽象方法。




