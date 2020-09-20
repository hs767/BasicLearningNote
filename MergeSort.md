## Merge Sort

Merge sort uses the idea that, if one can have a sorted left side and a sorted right side, then we can sort the whole thing by merging them. Therefore, we
can first divide the whole array into single elements, then merge the elements together. 

### A Simple Merge Sort
Here, I coded in a recursive way, therefore, left and right inputs are needed
```Merge Sort Code

public int[] mergeSort1(int[] ints, int left, int right) {
        int[] solution = new int[right - left + 1];

        if (left == right) {
            solution[0] = ints[left];
            return solution;
        }

        int mid = left + (right - left) / 2;
        int[] left_solu = mergeSort1(ints, left, mid);
        int[] right_solu = mergeSort1(ints, mid + 1, right);
        solution = combine(left_solu, right_solu);
        return solution;
    }
```

I also used a "combine" helper to combine two sorted arrays

```Combine helper code
public int[] combine (int[] a, int[] b) {
        int[] solu = new int[a.length + b.length];
        int i = 0, j = 0, count = 0;
        while (count < solu.length) {
            if (i == a.length) { //a is done
                //solu.add(b[j]);
                solu[count] = b[j];
                j++;
                count++;
            } else if (j == b.length) { //b is done
                //solu.add(a[i]);
                solu[count] = a[i];
                i++;
                count++;
            } else {
                if (a[i] < b[j]) {
                    //solu.add(a[i]);
                    solu[count] = a[i];
                    if (i < a.length) {
                        i++;
                    }
                } else {
                    //solu.add(b[j]);
                    solu[count] = b[j];
                    if (j < b.length) {
                        j++;
                    }
                }
                count++;
            }
        }
        //System.out.println(Arrays.toString(solu));
        return solu;
    }
```

