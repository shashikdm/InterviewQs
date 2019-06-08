## Question:  
accounts on FB are nodes in a global graph  
find degree of seperation between two arbitrary nodes  
## Hints:  
on average, the number of friends is 1000 so the *dos* is generally 2, 3, rarely 4, very very rarely more than 4  
doing BFS or DFS to search for B from A will take days because number of nodes increase by faction of 1000 at each level  
## Solution:  
Meet in the middle approach:  
- fb graph is bidirectional
- so we begin search from A as well as B
- Cases:
 - A == B return 0
 - B in friends(A) return 1
 - overlap(friends(A), friends(B)) return 2
 - overlap(friends(friends(A)), friends(B)) return 3
 - overlap(friends(friends(A)), friends(friends(B))) return 4
 - 5
 
time complexity O(M<sup>2</sup>log(M))