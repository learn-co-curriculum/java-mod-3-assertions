# Assertions

## Learning Goals

- Discuss static import.
- Learn about the different assertion methods.

## Introduction

In the last lesson, we were exposed to an assertion method, `assertEquals()`.
We saw how it could check and verify two different types of values: an expected
value and the actual value. This is crucial to unit testing since it can
immediately let us know if a test passed or failed when executed. In this
lesson, we will learn more about the different types of assertion methods that
can help us out when we are writing our unit tests!

## Static Import

The `Assertion` class is part of the `org.junit.jupiter.api` package and is a
collection of utility methods that support asserting conditions in unit tests.
In order to use the assertion methods of the `Assertion` class, we will need to
import it. But if we look at the code from our last lesson, this import
statement looks a little different:

```java
import static org.junit.jupiter.api.Assertions.*;
```

So what is happening here? As we know, in order to access static members, we
need to use a syntax like this:

```java
Assertions.assertEquals(2, 2);
```

But maybe we are going to use this method quite a bit in our test classes, and
we don't want the qualifying reference `Assertions` always attached to the
method. Perhaps we just want to call the method as such: `assertEquals(2,2)`. We
can then use a **static import** to access the static members of a class
without a qualifying reference:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
```

The syntax above will allow us to call the static `assertEquals()` method from
the `Assertions` class without specifying the class name prior to calling it!
But this import statement _only_ imports the `assertEquals()` method - not any
of the other assertion methods we may need to use. If we want to make use of
all the `Assertions` class' methods, we can do this:

```java
import static org.junit.jupiter.api.Assertions.*;
```

The asterisk, `*`, after the `Asertions.` will import _all_ the static
methods of the `Assertions` class. Now we can use any or all of the static
methods in our test class!

## Assertion Methods

Let's get into discussing the various utility assertion methods now in the
`Assertions` class!

### assertEquals

As we saw in our last lesson, the `assertEquals()` method takes in two arguments
of almost any data type! As we will see in several of these assertion methods,
the first parameter is the **expected** value and the second parameter is the
**actual** value that the method evaluated to. The `assertEquals()` method will
check that two arguments are "equal" to each other.

```java
@Test
void testEquals() {
    int expected = 2;
    int actual = 2;
    
    assertEquals(expected, actual);
}
```

It should also be noted that most assertion methods can take in more parameters,
such as a `String message` to display when the assertion fails:

```java
@Test
void testEquals() {
    int expected = 2;
    int actual = 2;
    
    assertEquals(expected, actual, "The integers are not equal.");
}
```

The third parameter is considered optional. Know that we can specify a message
like the one above if we choose to in any of these assertion methods we mention
today. But for the purposes of this lesson, we will look only at the required
arguments.

### assertNotEquals

Sometimes we want to make sure that two data types are _not_ equal to each
other. In unit testing, we can use the `assertNotEquals()` method then to check
the two arguments are indeed "not equal".

```java
@Test
void testNotEquals() {
    double unexpected = 2.99;
    double actual = 2.999;
    
    assertNotEquals(unexpected, actual);
}
```

### assertArrayEquals

If we want to make sure that two arrays are equal (in that every value in each
array is equal), we can use the `assertArrayEquals()` method! It will take in
two arrays of nearly any data type to compare.

```java
@Test
void testArrayEquals() {
    char[] expected = {'F', 'l', 'a', 't', 'i', 'r', 'o', 'n', ' ', 'S', 'c', 'h', 'o', 'o', 'l'};
    char[] actual = "Flatiron School".toCharArray();
    
    assertArrayEquals(expected, actual);
}
```

### assertTrue

Perhaps we want to ensure that a certain condition is true. We can use the
`assertTrue()` method to verify! Unlike the other assertion methods we have
seen, this method only takes in one required parameter and that is a condition
that can evaluate to a boolean.

```java
@Test
void testTrue() {
    boolean condition = 2 >= 1;
    assertTrue(condition);
}
```

### assertFalse

The complementary to the `assertTrue()` method is to assert that a condition is
false. If we want to verify that a condition evaluates to false, we can use the
`assertFalse()` method:

```java
@Test
void testFalse() {
    boolean condition = 2 < 1;
    assertFalse(condition);
}
```

### assertNull

In the last lesson, we briefly saw the `assertNull` method used when we were
checking to see if a method returned a `null` value. Instead of using the
`assertEquals()` method with the first parameter as `null`, we can just use this
method! It will then verify if a certain Java Object points to a `null` value in
memory.

```java
@Test
void testNull() {
    String actual = null;
    assertNull(actual);
}
```

### assertNotNull

Sometimes we want to ensure that an object is _not_ null. Like the
`assertNull()` method above, the `assertNotNull()` method will take in only one
required argument to verify the Java Object does not point to a `null` value:

```java
@Test
void testNull() {
    String actual = "Flatiron School";
    assertNotNull(actual);
}
```

## Summary

The assertion methods we reviewed in this lesson can also be found in the JUnit
documentation here:
[Assertions Class](https://junit.org/junit5/docs/5.7.2/api/org.junit.jupiter.api/org/junit/jupiter/api/Assertions.html)

Below is a table briefly summarizing the assertion methods covered in this
lesson that may you can use as a quick reference:

| Assertion                             | Description                                                                                        |
|---------------------------------------|----------------------------------------------------------------------------------------------------|
| `assertEquals(expected, actual)`      | Takes in two required arguments to assert that the expected value and actual value are equal       |
| `assertNotEquals(unexpected, actual)` | Takes in two required arguments to assert that the unexpected value and actual value are not equal |
| `assertArrayEquals(expected, actual)` | Takes in two required array arguments to assert that the expected array and actual array are equal |
| `assertTrue(condition)`               | Takes in one required boolean argument to assert that the condition is true                        |
| `assertFalse(condition)`              | Takes in one required boolean argument to assert that the condition is false                       |
| `assertNull(actual)`                  | Takes in one required object to assert that the actual is `null`                                   |
| `assertNotNull(actual)`               | Takes in one required object to assert that the actual is not `null`                               |

## Resources

[Assertions Class](https://junit.org/junit5/docs/5.7.2/api/org.junit.jupiter.api/org/junit/jupiter/api/Assertions.html)
