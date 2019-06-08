<div ng-bind-html="trustedHtml" class="ng-binding"><p>Given an unsorted integer array, find the first missing positive integer.</p>
<p><strong>Example:</strong></p>
<p>Given <code>[1,2,0]</code> return 3,</p>
<p><code>[3,4,-1,1]</code> return 2, </p>
<p><code>[-8, -7, -6]</code> returns 1 </p>
<p>Your algorithm should run in <code>O(n)</code> time and use constant space.</p></div>

## Solution
number lies between 1 and n+1
so use counting sort
- ignore arr[i] < 1 and arr[i] > n
place arr[i] to its correct position and swap with i
if arr[i] is alright or arr[i] is to be ignored then move on

## Code
```
int Solution::firstMissingPositive(vector<int> &A) {
    long i = 0, N = A.size(), temp;
    while(i < N)
    {
        if(A[i] == i+1 || A[i] < 1 || A[i] > N)
        {
            i++;
        }
        else if(A[i] >= 1 && A[i] <= N)
        {
            if(A[A[i]-1] != A[i])
            {
                temp = A[i];
                A[i] = A[temp-1];
                A[temp-1] = temp;
            }
            else
            {
                i++;
            }
        }
        else
        {
            i++;
        }
    }
    for(i = 0; i < N; i++)
    {
        if(A[i] != i+1)
        {
            return i+1;
        }
    }
    return N+1;
}
```