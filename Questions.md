**What is the time complexity of Euclid's GCD algorithm?**

Euclidean algorithm by subtraction

```python
1 def gcd(a, b):
2 	if a == b:
3 		return a
4 	if a > b:
5 		gcd(a - b, b)
6 	else:
7 		gcd(a, b - a)
```

Let’s estimate this algorithm’s time complexity (based on n = a+b). The number of steps can
be linear, for e.g. gcd(x, 1), so the time complexity is O(n). This is the worst-case complexity,
because the value x + y decreases with every step.



 Euclidean algorithm by division

```python
1 def gcd(a, b):
2 	if a % b == 0:
3 		return b
4	else:
5 		return gcd(b, a % b)
```

[Solution Quora](https://qr.ae/TWtAoq)

consider  **a** = Fibonacci(N) and **b** = Fibonacci(N-1)

Fibonacci(N) = Fibonacci(N-1) + Fibonacci(N-2)



gcd(**a**,**b**) = gcd(**b**,**a**mod**b**)

​				= gcd(Fibonacci(N-1),Fibonacci(N-2)) 

​				= gcd(Fibonacci(N-2),Fibonacci(N-3))

Therefore total no of steps = N

Now Fibonacci(N) can approximately be evaluated as power of golden numbers, so N can be expressed as logarithm of Fibonacci(N) or a.

![{\displaystyle F_{n}=\left[{\frac {\varphi ^{n}}{\sqrt {5}}}\right],\ n\geq 0,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f284c42fe2e2d38c49ba4d1a8a3f16eb5afed8ed)

In other words O(N) can be rewritten as O(log(a)).

 

