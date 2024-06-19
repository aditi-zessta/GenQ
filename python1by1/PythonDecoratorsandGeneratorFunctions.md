QUESTION 5


# prompt 9, result 2
# Question 2




# 0 - Topics : Python Decorators and Generator Functions




# 1 - Scenario : Caching the results of a function that yields multiple values using a decorator




# 2 - Code :




# ```python
def cache(func):
    results = {}
    def wrapper(*args):
        if args not in results:
            results[args] = func(*args)
        return results[args]
    return wrapper




@cache
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b




for i in fib(10):
    print(i)
```




# 3 - Question : The above code is supposed to cache the results of the Fibonacci generator function, but it doesn't work
#  as expected. What is the issue?




# 4 - Explanation : The issue is that the `cache` decorator is trying to cache the generator object itself, not the
#  it produces. When the generator function is called again with the same arguments, it returns the cached generator object,
#  which is already exhausted, thus producing no values.




# 5 - Answer :




# ```python
def cache(func):
    results = {}
    def wrapper(*args):
        if args not in results:
            results[args] = list(func(*args))
        return results[args]
    return wrapper




@cache
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b




for i in fib(10):
    print(i)
```




# In the corrected code, we convert the generator to a list before caching it, thus storing the actual values it produces.




# ---
