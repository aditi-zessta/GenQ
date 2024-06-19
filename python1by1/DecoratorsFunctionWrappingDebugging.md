QUESTION 4
# Question 2:




# - **Topics**: Decorators, Function Wrapping, Debugging
# - **Scenario**: A Python developer is trying to create a decorator that will log the execution time of a function.
#  However, the decorator is not working as expected.
# - **Code**:
# ```python
import time




def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        func(*args, **kwargs)
        end = time.time()
        print(f'{func.__name__} ran in: {end - start} sec')
    return func




@timer
def long_running_function():
    time.sleep(5)




long_running_function()
```
# - **Question**: The timer decorator is not working as expected. What is wrong with this code and how can it be fixed?
# - **Explanation**: The timer function is not returning the wrapper function, it is returning the original function instead.
#  This means the timing code will never be run.
# - **Answer**:
# ```python
import time




def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        func(*args, **kwargs)
        end = time.time()
        print(f'{func.__name__} ran in: {end - start} sec')
    return wrapper




@timer
def long_running_function():
    time.sleep(5)




long_running_function()
```
