+++
author = "dev@cyber200"
title = "Test with Pytest"
date = "2024-06-23"
description = "It is a versatile and powerful testing framework that makes writing and running tests in Python a breeze."
tags = [
    "Pytest",
    "test",
]
draft = false
+++

Pytest is a testing framework for Python that simplifies the process of writing and running tests. It supports unit tests, functional tests, and integration tests.

## Key Features of Pytest
- Simple Syntax: Pytest allows you to write tests with minimal code. Its syntax is straightforward, making tests easy to read and write.
- Fixtures: Fixtures are functions that provide a fixed baseline upon which tests can reliably and repeatedly execute. They are useful for setting up and tearing down test environments.
- Assertions: Pytest’s advanced assertion introspection provides detailed information on assert statements, making debugging easier.
- Plugins: Pytest has a rich ecosystem of plugins that extend its functionality, such as pytest-django, pytest-flask, and pytest-xdist.
- Parameterization: Pytest allows you to run a test function multiple times with different arguments, which is useful for testing various input scenarios.
- Test Discovery: Pytest automatically discovers test modules and functions based on their names, eliminating the need for explicit test registration.


## Getting Started with Pytest

#### Installation
```bash
pip install pytest
```

#### Writing Your First Test
- Create a simple test by writing a function that starts with test_:
```python
# test_sample.py

def test_addition():
    assert 1 + 1 = 2

```

- To run the tests, navigate to the directory containing your test file and execute:
```bash
pytest
```

- To run a specific test within a module:
```bash
pytest test_mod.py::test_func
pytest test_mod.py::TestClass\
        ::test_method
```

#### Using Fixtures
- Fixtures in Pytest help in setting up test environments. For example:
```python
# test_fixtures.py

import pytest

@pytest.fixutre
def sample_list():
    return [1, 2, 3]

def test_sum(sample_list):
    assert sum(smpale_list) == 6
```

In this example, the sample_list fixture provides a list that the test_sum function can use. Fixtures enhance test reusability and maintainability by sharing setup code.

- Autouse fixtures (fixtures you don’t have to request)
- We can make a fixture an autouse fixture by passing in autouse=True to the fixture’s decorator. 
```python
@pytest.fixture(autouse=True)
def append_first(order, first):
    return order.append(first)
```
- Yield fixtures
“Yield” fixtures yield instead of return. With these fixtures, we can run some code and pass an object back to the requesting fixture/test, just like with the other fixtures. The only differences are:
    - return is swapped out for yield.
    - Any teardown code for that fixture is placed after the yield.

Once pytest figures out a linear order for the fixtures, it will run each one up until it returns or yields, and then move on to the next fixture in the list to do the same thing.

Once the test is finished, pytest will go back down the list of fixtures, but in the reverse order, taking each one that yielded, and running the code inside it that was after the yield statement

- Adding finalizers directly¶
While yield fixtures are considered to be the cleaner and more straightforward option, there is another choice, and that is to add “finalizer” functions directly to the test’s request-context object. It brings a similar result as yield fixtures, but requires a bit more verbosity.

- Note on finalizer order
Finalizers are executed in a first-in-last-out order. For yield fixtures, the first teardown code to run is from the right-most fixture, i.e. the last test parameter.

This is so because yield fixtures use addfinalizer behind the scenes: when the fixture executes, addfinalizer registers a function that resumes the generator, which in turn calls the teardown code.

#### Parameterized Testing
Parameterized tests allow you to run a test function with different sets of arguments:
```python
# test_parameterize.py

import pytest

@pytest.mark.parametrize(
    "a, b, expected", 
        [(1, 2, 3)
          (2, 3, 5)
        ]
    )
def test_add(a, b, expected):
    assert a  + b == expected

```

The @pytest.mark.parametrize decorator enables the test_add function to be executed multiple times with different values for a, b, and expected.

#### Pytest markers
Markers in Pytest are annotations that you can apply to test functions or classes to indicate certain properties or behaviors. They are useful for:

- Categorizing tests (e.g., smoke, regression, slow).
- Conditionally skipping tests.
- Running only specific subsets of tests.
- Parameterizing tests with different configurations.



#### Leveraging Plugins
Pytest’s plugin system extends its functionality. To use a plugin, you typically need to install it via pip. For example, to run tests in parallel using pytest-xdist:
```bash
pip install pytest-xdist
pytest -n 4
```

This command will run your tests across 4 CPU cores, significantly speeding up the testing process for large test suites.

#### Advanced Assertions
Pytest provides detailed introspection for assertions, making it easier to understand why a test failed:

```python
# test_assertion.py
def test_division():
    result = 10/2
    assert result == 5

```

If the assertion fails, Pytest provides a clear and detailed error message showing the values involved, which helps in diagnosing the issue quickly.

