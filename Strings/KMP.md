<div ng-bind-html="trustedHtml" class="ng-binding"><p><strong>Implement strStr().</strong></p>
<blockquote>
  <p>strstr - locate a substring ( needle ) in a string ( haystack ).</p>
</blockquote>
<p><strong>Try not to use standard library string functions for this question.</strong></p>
<p>Returns the index of the first occurrence of needle in haystack, or <code>-1</code> if needle is not part of haystack.</p>
<blockquote>
  <p><strong>NOTE:</strong></p>
  <p><strong>Good clarification questions:</strong></p>
  <ol>
  <li><p>What should be the return value if the needle is empty?</p></li>
  <li><p>What if both haystack and needle are empty?</p></li>
  </ol>
  <p>For the purpose of this problem, assume that the return value should be -1 in both cases.</p>
</blockquote></div>

# Solution:
## KMP
1. precompute Longest Prefix which is also Suffix lps array 2ptr approach O(m)
2. use lps to match both strings 2ptr approach O(n)

# Code
```
void display(vector<int> &x)
{
    for(int i = 0; i < x.size(); i++) cout<<x[i]<<' ';
    cout<<'\n';
}
int Solution::strStr(const string A, const string B) {
    if(A.empty() || B.empty()) return -1;
    //KMP
    //Precomputation
    int n = A.length(), m =  B.length(), i, j;
    if(m > n) return -1;
    vector<int> lps(m);
    lps[0] = 0;
    i = 0; j = 1;
    while(i < m && j < m)
    {
        if(B[j] == B[i])
        {
            lps[j] = i+1;
            i++;
            j++;
        }
        else
        {
            if(i == 0)
            {
                lps[j] = 0;
                j++;
            }
            else
            {
                i = lps[i-1];
            }
        }
    }
    //matching
    //display(lps);
    i = 0;
    j = 0;
    while(i < n)
    {
        //cout<<i<<' '<<j<<'\n';
        if(A[i] == B[j])
        {
            i++;
            j++;
        }
        else
        {
            if(j > 0)
            {
                j = lps[j-1];
            }
            else
            {
                j = 0;
                i++;
            }
        }
        if(j == m)
        {
            return i-m;
            j = lps[j];
            i++;
        }
    }
    return -1;
}
```