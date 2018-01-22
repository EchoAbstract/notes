# Useful C++ Snippets


## Operator Overloads

`T` refers to your `class` or `struct`.

### Out of class

    std::ostream& operator<<(std::ostream& os, const T& t); // << operator

### Friendly

    friend std::ostream& operator<<(std::ostream& os, const T& t); // << operator
