# Coveragable Code Principle
You need to write coveragable code.

You have a code like:
```py
print("hello world")
```

`print` method is already coverage by tests in python source code. That means you can write a function with it like:

```py
def say_hello():
    print("hello world")  # tested
```

Now you have a coveragable function. We need to write test for it.
What if i write another function like:

```py
def conversation():
    say_hello()  # assume that you did not write its test
    print("hi")  # tested
```

You write a function named as `conversation` and it has untested line.
Coveragable Code Principle says:
1. You can not write a function with untested code parts.
2. All functions needs its test.
3. Every function can be valid if all sub lines tested before.
