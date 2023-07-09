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

Lets fix `conversation` function with write tests with `say_hello`.

```py
import unittest
from io import StringIO
import sys

# Functions
def say_hello():
    print("hello world")  # tested

def conversation():
    say_hello()  # tested
    print("hi")  # tested

# Test Case
class TestSayHello(unittest.TestCase):
    def test_say_hello(self):
        # Temporarily replace standard output
        capturedOutput = StringIO()
        sys.stdout = capturedOutput

        # Call the function
        say_hello()

        # Reset standard output
        sys.stdout = sys.__stdout__

        # Check if the function print "hello world" followed by a newline character
        self.assertEqual(capturedOutput.getvalue(), "hello world\n")

if __name__ == '__main__':
    unittest.main()
```

Now all is coveraged by tests.
Now our function is coveragable.
