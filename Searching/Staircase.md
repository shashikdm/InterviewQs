<p>Given an integer <strong>A</strong> representing the square blocks. The height of each square block is <strong>1</strong>.
The task is to create a staircase of max height using these blocks.</p>
<p>The first stair would require only one block, the second stair would require two blocks and so on.</p>
<p>Find and return the maximum height of the staircase.</p>
<p><br>
<strong>Input Format</strong></p>
<pre><code>The only argument given is integer A.
</code></pre>
<p><strong>Output Format</strong></p>
<pre><code>Return the maximum height of the staircase using these blocks.
</code></pre>
<p><strong>Constraints</strong></p>
<pre><code>0 &lt;= A &lt;= 10^9
</code></pre>
<p><strong>For Example</strong></p>
<pre><code>Input 1:
    A = 10
Output 1:
    4

Input 2:
    A = 20
Output 2:
    5
</code></pre>

**Solution**  
Do binary search over the solution space. look for sum <= A and nexsum > A

**Tips**
- Take care of overflow, use long

**Code**
```
int Solution::solve(int A) {
    long low = 0, high = A, mid, midsum, nextmidsum;
    while(true)
    {
        mid = low+(high-low)/2;
        midsum = mid*(mid+1)/2;
        nextmidsum = midsum+mid+1;
        if(midsum <= A && nextmidsum > A)
        {
            break;
        }
        if(midsum > A)
        {
            high = mid-1;
        }
        else if(nextmidsum <= A)
        {
            low = mid+1;
        }
    }
    return mid;
}
```
