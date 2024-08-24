# node-complex-data-type-from-fortran
A node example of taking complex data type from Fortran
```fortran
MODULE ComplexModule
  IMPLICIT NONE
  TYPE :: ComplexType
     REAL :: real, imag
  CONTAINS
     OPERATOR(+) (a, b) RESULT(c)
       TYPE(ComplexType), INTENT(IN) :: a, b
       TYPE(ComplexType) :: c
       c%real = a%real + b%real
       c%imag = a%imag + b%imag
     END OPERATOR
  END TYPE ComplexType
END MODULE ComplexModule
```

### What Language Is This Written In?

The code snippet is written in **Fortran**, a programming language commonly used in scientific and engineering computations. It defines a module with a user-defined data type for representing complex numbers and overloads the addition operator (`+`) for this data type.

### What Does This Code Snippet Do?

This code snippet creates a module named `ComplexModule` that defines a custom data type called `ComplexType` to represent complex numbers. It then overloads the `+` operator to allow addition of two `ComplexType` instances, i.e., adding the real parts and imaginary parts of two complex numbers separately.

### How It Works

- **Module and Data Type Declaration:**
  - `MODULE ComplexModule`: Declares a module named `ComplexModule` to encapsulate related definitions and functionalities.
  - `TYPE :: ComplexType`: Defines a custom data type `ComplexType` that consists of two `REAL` (floating-point) components: `real` and `imag`, representing the real and imaginary parts of a complex number.
  
- **Operator Overloading:**
  - `OPERATOR(+) (a, b) RESULT(c)`: This defines an overloaded `+` operator for the `ComplexType`. It allows adding two complex numbers (of type `ComplexType`) by adding their real and imaginary parts separately.
  - `a%real + b%real`: Adds the real parts of the two complex numbers `a` and `b`.
  - `a%imag + b%imag`: Adds the imaginary parts of the two complex numbers `a` and `b`.
  - `c%real`, `c%imag`: Stores the results in a new `ComplexType` instance `c`, which is then returned as the result of the addition.

### Node.js Version

To implement the equivalent functionality in Node.js (JavaScript), you can define a `ComplexNumber` class and overload the addition operator using a method:

```javascript
class ComplexNumber {
  constructor(real, imag) {
    this.real = real;
    this.imag = imag;
  }

  // Method to add two ComplexNumber instances
  add(other) {
    return new ComplexNumber(
      this.real + other.real,
      this.imag + other.imag
    );
  }

  // Custom toString method to display the complex number
  toString() {
    return `${this.real} + ${this.imag}i`;
  }
}

// Example usage:
const complex1 = new ComplexNumber(1.5, 2.5);
const complex2 = new ComplexNumber(3.0, 4.0);

const result = complex1.add(complex2);

console.log(`Result: ${result}`); // Output: Result: 4.5 + 6.5i
```

### How the Node.js Version Works

- **Class Definition:**
  - `ComplexNumber` is a class that represents a complex number with `real` and `imag` properties for the real and imaginary parts.

- **Addition Method:**
  - The `add` method takes another `ComplexNumber` instance as a parameter and returns a new `ComplexNumber` instance. The new instance contains the sum of the real parts and the sum of the imaginary parts.

- **Custom toString Method:**
  - The `toString` method formats the complex number as a string in the form of "a + bi", making it easier to print the result.

- **Example Usage:**
  - Two instances of `ComplexNumber` are created (`complex1` and `complex2`), and their sum is computed using the `add` method. The result is then displayed using the `toString` method.
