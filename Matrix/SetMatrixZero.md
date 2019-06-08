<div ng-bind-html="trustedHtml" class="ng-binding"><p>Given an <strong>m x n matrix</strong> of 0s and 1s, if an element is 0, set its entire row and column to 0. </p>
<p>Do it in place.</p>
<p><strong>Example</strong></p>
<p>Given array A as </p>
<pre><code>1 0 1
1 1 1 
1 1 1
</code></pre>
<p>On returning, the array A should be : </p>
<pre><code>0 0 0
1 0 1
1 0 1
</code></pre>
<p><em>Note that this will be evaluated on the extra memory used. Try to minimize the space and time complexity.</em> </p></div>

## Solution
save rows and columns to be zeroed in one pass
```
void Solution::setZeroes(vector<vector<int> > &A) {
    long m = A.size(), n = A[0].size(), i, j, k, I, J;
    vector<long> rows;
    vector<long> columns;
    for(i = 0; i < m; i++)
    {
        for(j = 0; j < n; j++)
        {
            if(!A[i][j])
            {
                if(find(columns.begin(), columns.end(), j) == columns.end())
                {
                    columns.push_back(j);
                }
                if(find(rows.begin(), rows.end(), i) == rows.end())
                {
                    rows.push_back(i);
                }
            }
        }
    }
    for(i = 0; i < rows.size(); i++)
    {
        for(j = 0; j < n; j++)
        {
            A[rows[i]][j] = 0;
        }
    }
    for(j = 0; j < columns.size(); j++)
    {
        for(i = 0; i < m; i++)
        {
            A[i][columns[j]] = 0;
        }
    }
}
```