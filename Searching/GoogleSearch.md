## Question
You are given prefix of the search query
return the top 5 search query suggestions

## Hint
use of Tries

## Solution
- Make Trie and store top 5 search and frequency at each node
- to update frequency go till final result say "michael".
- inc frequency of michael in michael by one
- traverse back and inc same. if it doesn't exist in top 5 then compare least frequent in top5 with michael
- Storage required will be huge so split the storage as follows
### things to keep in mind when splitting storage
- you should minimize machine hops
- distribute storage evenly
- distribute load(requests) evenly 