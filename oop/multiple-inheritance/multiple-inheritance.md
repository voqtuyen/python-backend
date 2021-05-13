# Multiple Inheritance in Python
- Multiple inheritance
- Diamond inheritance problem
- Method resolution order (MRO)

## Multiple Inheritance
- Python supports **inheritance** from **multiple classes**
    ```python3
    class A:
        pass

    class B:
        pass

    class C:
        pass

    class ABC(A, B, C)
        pass
    ```
- Multiple inheritance is a feature of object-oriented programming language in which an object or class can inherit characteristics and features from more than one parent object or parent class.

- In single inheritance, an object or class may only inherit from one particular object or class.

## Diamond inheritance problem
- Diamond inheritance problem arises when two classes B and C inherit from A and class D inherits from both B and C.
- If there is a method in A that B and C have overidden and D does not override it, then which version of the method does D inherit? That of B or that of C?

    ![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Diamond_inheritance.svg/220px-Diamond_inheritance.svg.png)

## Method resolution order (MRO)


## Reference
1. https://youtu.be/SqzziP_ZtuU
