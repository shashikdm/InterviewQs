<div ng-bind-html="trustedHtml" class="ng-binding"><p>You are given a read only array of n integers from 1 to n. </p>
<p>Each integer appears exactly once except A which appears twice and B which is missing.</p>
<p>Return A and B. </p>
<p><em>Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</em></p>
<p><em>Note that in your output A should precede B.</em> </p>
<p><strong>Example:</strong> </p>
<pre><code>Input:[3 1 2 5 3] 

Output:[3, 4] 

A = 3, B = 4
</code></pre></div>
## Solution
let missing number be A
let repeat number be B
```
n*(n+1)/2 = sum(arr) - A + B
n*(n+1)*(2*n+1)/6 = sumsqr(arr) - A*A + B*B = sumsqr(arr) + (B-A)(B+A)
//two equations two variables
```
Be careful with the overflow
## Code
```
vector<int> Solution::repeatedNumber(const vector<int> &A) {
    unsigned long long N = A.size(), i;
    int X, Y;
    long double R = 0, D = 0;
    for(i = 0; i < N; i++)
    {
        D = D + A[i]-i-1;
        R = R - (unsigned long long)A[i]*A[i] + (i+1)*(i+1);
    }
    X = round((round(R/D)+D)/2);
    Y = X-D;
    return vector<int> {-Y, -X};
}
```
