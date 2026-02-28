//merge

#include <iostream>
using namespace std;

void merge(int arr[], int st, int mid, int end) {
    int temp[end - st + 1];
    int i = st, j = mid + 1, idx = 0;
    
    cout << "in redme";
    while (i <= mid && j <= end) {
        if (arr[i] < arr[j]) {
            temp[idx++] = arr[i++];
        } else {
            temp[idx++] = arr[j++];
        }
    }

    while (i <= mid) {
        temp[idx++] = arr[i++];
    }

    while (j <= end) {
        temp[idx++] = arr[j++];
    }

    for (int k = 0; k < end - st + 1; k++) {
        arr[st + k] = temp[k];
    }
}

void mergeSort(int arr[], int st, int end) {
    if (st < end) {
        int mid = st + (end - st) / 2;
        mergeSort(arr, st, mid);
        mergeSort(arr, mid + 1, end);
        merge(arr, st, mid, end);
    }
}

void printArr(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {13, 6, 7, 5, 8, 1, 3, 4};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    printArr(arr, n);

    mergeSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    printArr(arr, n);

    return 0;
}
