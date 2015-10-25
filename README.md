# MergeSort
public class mergeSort {
     
    private int[] array;
    private int[] tempmergArr;
    private int length;
 
    public static void main(String a[]){
         
        int[] inputArr = {10,34,2,56,7,67,88,42};
        mergeSort mms = new mergeSort();
        mms.sort(inputArr);
        for(int i:inputArr){
            System.out.print(i);
            System.out.print(" ");
        }
    }
     
    public void sort(int inputArr[]) {
        this.array = inputArr;
        this.length = inputArr.length;
        this.tempmergArr = new int[length];
        domergeSort(0, length - 1);
    }
 
    private void domergeSort(int lowerIndex, int higherIndex) {
         
        if (lowerIndex < higherIndex) {
            int middle = lowerIndex + (higherIndex - lowerIndex) / 2;
            domergeSort(lowerIndex, middle);
            domergeSort(middle + 1, higherIndex);
            mergeParts(lowerIndex, middle, higherIndex);
        }
    }
 
    private void mergeParts(int lowerIndex, int middle, int higherIndex) {
 
        for (int i = lowerIndex; i <= higherIndex; i++) {
            tempmergArr[i] = array[i];
        }
        int i = lowerIndex;
        int j = middle + 1;
        int k = lowerIndex;
        while (i <= middle && j <= higherIndex) {
            if (tempmergArr[i] <= tempmergArr[j]) {
                array[k] = tempmergArr[i];
                i++;
            } else {
                array[k] = tempmergArr[j];
                j++;
            }
            k++;
        }
        while (i <= middle) {
            array[k] = tempmergArr[i];
            k++;
            i++;
        }
 
    }
}
