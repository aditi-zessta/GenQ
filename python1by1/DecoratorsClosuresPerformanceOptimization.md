QUESTION 2
# # #prompt6, gpt4, temp = 0.7
# Question 2

# 0 - Topics: Decorators, Closures, Performance Optimization


# 1 - Scenario: A team is working on a performance-critical application where function execution time is very important.
#  The team lead wants to have a mechanism to measure the execution time of all the functions in the application. A junior
#  developer tried to use decorators for the same but facing some issues.


# 2 - Code:
# ```python
import time




def timer_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.perf_counter()
        result = func(args, kwargs)
        end_time = time.perf_counter()
        print(f"Function {func.__name__} took {end_time - start_time} seconds to execute")
        return result
    return wrapper




@timer_decorator
def sum_numbers(n):
    return sum(range(n))




print(sum_numbers(1000000))
# ```


# 3 - Question: The above code is not working as expected. Can you find out the mistake and correct it?


# 4 - Explanation: The problem is with the function call inside the wrapper function. The arguments are not passed
#  correctly to the function. Instead of passing `args` and `kwargs` as two separate arguments, it should be unpacked
# while calling the function.


# 5 - Answer:
# ```python
import time


def timer_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.perf_counter()
        result = func(*args, **kwargs)
        end_time = time.perf_counter()
        print(f"Function {func.__name__} took {end_time - start_time} seconds to execute")
        return result
    return wrapper


@timer_decorator
def sum_numbers(n):
    return sum(range(n))


print(sum_numbers(1000000))
# ```
